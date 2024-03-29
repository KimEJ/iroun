<template>
    <section class="pt-20 md:pt-24 relative">
        <AtomsContainer>
            <div class="flex justify-between items-center pb-6">
                <div class="">
                    <AtomsTitle texte="진행중인 프로젝트" />
                </div>
                <div class="flex items-center min-w-max relative">
                    <AtomsLinkBtn href="/archive" variant="primary">
                        지난 프로젝트 보기
                    </AtomsLinkBtn>
                </div>
            </div>
            <div class="relative">
                <!--  -->
                <div class="flex absolute top-1/2 -left-5 -translate-y-1/2 z-10 transition duration-300 ease-linear"
                    :class="prevIsVisible ? 'visible opacity-100' : 'insisible opacity-0'">
                    <AtomsSwiperNavButton @click="scrollToLeft()">
                        <IconsPrevIco />
                    </AtomsSwiperNavButton>
                </div><!--  -->
                <div class="flex absolute top-1/2 -right-5 -translate-y-1/2 z-10 transition duration-300 ease-linear"
                    :class="nextIsVisible ? 'visible opacity-100' : 'insisible opacity-0'">
                    <AtomsSwiperNavButton @click="scrollToRight()">
                        <IconsNextIco />
                    </AtomsSwiperNavButton>
                </div>

                <div data-slide-recent @scroll="initScroll()"
                    class="flex items-stretch gap-5 overflow-hidden overflow-x-auto invisible-scroll">
                    <div v-for="post in recentData" :key="post.title"
                        class=" w-11/12 min-w-[91.666667%] xs:w-80 xs:min-w-[20rem] md:w-1/3 md:min-w-[33.333333%] lg:w-1/4 lg:min-w-[25%]">
                        <CardsProject :title='post.title' :description="post.description" :timestamp='post.timestamp'
                            :href='post.href' :cover-image='post.coverImage' />
                    </div>
                </div>
            </div>
        </AtomsContainer>
    </section>
</template>

<script lang="ts" setup>
const { data } = await useAsyncData('home', () => queryContent('/projects').sort({ _id: -1 }).find())

const nextIsVisible = useState('nextIsVisible', () => false)
const prevIsVisible = useState('prevIsVisible', () => false)

const elementPerPage = ref(5)

const formattedData = computed(() => {
    return data.value?.map((articles) => {
        return {
            href: articles._path,
            title: articles.title || 'no-title available',
            description: articles.description || 'no-description available',
            coverImage: articles.image || '/not-found.jpg',
            timestamp: new Date(articles.date).toLocaleDateString() || 'not-date-available',
        }
    }) || []
})

const recentData = computed(() => {
    return formattedData.value.filter((data, idx) => {
        const startInd = 0
        const endInd = elementPerPage.value - 1

        if (idx >= startInd && idx <= endInd)
            return true
        else return false
    }) || []
})

let element: HTMLDivElement
if (typeof document !== "undefined") {
    element = document.querySelector("[data-slide-recent]") as HTMLDivElement
}
function initScroll(): void {
    if (typeof element === "undefined" || element === null) {
        return
    }
    prevIsVisible.value = element.scrollLeft <= 0 ? false : true
    nextIsVisible.value = element.scrollLeft >= element.scrollWidth - element.offsetWidth - 1 ? false : true
}

function scrollToLeft(): void {
    if (typeof element === "undefined" || element === null) {
        return
    }
    element.scrollLeft -= element.clientWidth
}

function scrollToRight(): void {
    if (typeof element === "undefined" || element === null) {
        return
    }
    element.scrollLeft += element.clientWidth
}

onMounted(() => {
    if (window !== null) {
        initScroll()
    }
})
</script>