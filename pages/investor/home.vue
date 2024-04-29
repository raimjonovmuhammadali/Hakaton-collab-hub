<script setup lang="ts">
definePageMeta({
    layout: 'main',
});
useHead({
    title: 'Collab Hub | Home'
})


const items = [
    'https://picsum.photos/1920/1080?random=1',
    'https://picsum.photos/1920/1080?random=2',
    'https://picsum.photos/1920/1080?random=3',
    'https://picsum.photos/1920/1080?random=4',
    'https://picsum.photos/1920/1080?random=5',
    'https://picsum.photos/1920/1080?random=6'
]

const carouselRef = ref()

onMounted(() => {
    setInterval(() => {
        if (!carouselRef.value) return

        if (carouselRef.value.page === carouselRef.value.pages) {
            return carouselRef.value.select(0)
        }

        carouselRef.value.next()
    }, 5000)
})

</script>
<template>
    <main class="bg-white">
        <!-- OUR section -->
        <section class="w-full h-[75vh] pt-[5vh] bg-[#EBF5F3] relative">

            <div class="w-[85%] mx-auto flex items-center justify-between  gap-4 rounded-md">
                <UCarousel ref="carouselRef" v-slot="{ item }" :items="items" :ui="{ item: 'basis-full' }"
                    class="rounded-lg overflow-hidden w-full h-[450px] relative" indicators>
                    <img :src="item" class="w-full h-screen" draggable="false">
                </UCarousel>
            </div>
        </section>

        <!-- Projects section -->
        <section class="w-[85%] mx-auto flex flex-col items-center justify-between  gap-4  p-5 rounded-md mt-10">
            <h1 class="text-4xl font-semibold text-black my-4">Start<span class="text-green-400">ups</span></h1>
            <div class="w-full flex items-center justify-between flex-wrap gap-4">
                <UiStartups/>
            </div>
        </section>
    </main>
</template>