<template>
    <section class="pt-20 md:pt-24">
        <AtomsContainer>
            <div class="grid md:grid-cols-2 gap-10 xl:gap-14 relative">
                <div class="flex md:h-full ">
                    <div
                        class="w-full md:h-full rounded-3xl bg-white dark:bg-body shadow-lg shadow-box-shadow border border-box-border">
                        <img src="/images/TyLw3IQALMs.jpg" alt="Illustratuin about" width="500"
                            class="w-full h-full object-cover rounded-2xl">
                    </div>
                </div>
                <div class="md:py-2 lg:py-4 relative">
                    <div class="absolute right-0 top-0 h-full w-full flex justify-end">
                        <span class="flex opacity-20">
                            <span class="w-16 h-32 rounded-l-full flex bg-primary blur-2xl"></span>
                            <span class="w-16 h-32 rounded-r-full flex bg-[#f88fc2] blur-2xl mt-14"></span>
                        </span>
                    </div>
                    <div class="relative">
                        <AtomsTitle texte="같은 꿈을 꾸는 이룸이를 찾습니다." />
                        <p class="text-gray-600 dark:text-gray-300 pt-8">
                            이룸이는 아이들이 행복한 세상을 이루기 위해 노력하는 사람들입니다.<br />
                            저희와 같은 꿈을 꾸는 재능있는 이룸이를 찾습니다.<br />
                            아주 작은 일이라도 괜찮습니다. 저희와 같이 이룸이가 되어주세요.
                        </p>
                        <div class="grid grid-cols-3 gap-4 max-w-lg pt-8">
                            <!-- <div
                                v-for="card in cards"
                                class="text-center rounded-xl bg-box-bg shadow-lg shadow-box-shadow border border-box-border p-3">
                                <h3 class="text-gray-800 dark:text-white font-bold text-xl sm:text-2xl lg:text-3xl">+ {{ card.count }}
                                </h3>
                                <p class="text-sm sm:text-base text-gray-600 dark:text-gray-300">{{ card.title }}</p>
                            </div> -->
                        </div>
                        <div class="pt-10 flex">
                            <AtomsLinkBtn href="/projects/2024-03-06" variant="primary">
                                이룸이가 되기
                            </AtomsLinkBtn>
                        </div>
                    </div>
                </div>
            </div>
        </AtomsContainer>
    </section>
</template>

<script lang="ts" setup>
const cards = [
    {
        count: 45,
        title: "개의 프로젝트",
    },
    {
        count: 500,
        title: "명의 아이들",
    },
    {
        count: 5,
        title: "명의 이룸이",
    },
]
</script>