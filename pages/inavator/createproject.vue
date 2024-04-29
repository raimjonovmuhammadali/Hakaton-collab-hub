<script setup lang="ts">
definePageMeta({
    layout: 'main',
});
useHead({
    title: 'Collab Hub | Home'
})
</script>
<template>
    <div class="w-full mx-auto flex items-center justify-center">


        <div class="w-full min-h-screen p-6 bg-[#EBF5F3] flex items-center justify-center text-black">
            <div class="container max-w-screen-lg mx-auto">
                <div>
                    <h2 class="font-semibold text-xl text-gray-600">Loyiha qo'shish</h2>
                    <p class="text-gray-500 mb-6">Yangi loyihangizni qo'shing</p>

                    <div class="bg-white rounded shadow-lg p-4 px-4 md:p-8 mb-6">
                        <div class="grid gap-4 gap-y-2 text-sm grid-cols-1 lg:grid-cols-3">

                            <div class="lg:col-span-2">
                                <div class="grid gap-4 gap-y-2 text-sm grid-cols-1 md:grid-cols-5">
                                    <div class="md:col-span-5">
                                        <label for="full_name">Nom bering</label>
                                        <input type="text" name="full_name" id="full_name"
                                            class="h-10 border mt-1 rounded px-4 w-full bg-gray-50" value="" />
                                    </div>

                                    <div class="md:col-span-5">
                                        <label for="email">Tavsif</label>
                                        <textarea ype="text" name="email" id="email"
                                            class="h-10 border mt-1 rounded px-4 w-full bg-gray-50" value="" ></textarea>
                                    </div>
                                    <div class="md:col-span-5">
                                        <label for="full_name">Video uchun havola</label>
                                        <input type="text" name="full_name" id="full_name"
                                            class="h-10 border mt-1 rounded px-4 w-full bg-gray-50" value="" />
                                    </div>

                                    
                                    <div class="md:col-span-2">
                                        <label for="city">Eng kam summa</label>
                                        <input type="text" name="city" id="city"
                                        class="h-10 border mt-1 rounded px-4 w-full bg-gray-50" value=""
                                        placeholder="" />
                                    </div>
                                    <div class="md:col-span-3">
                                        <label for="address">Taqdimot yuklang</label>
                                        <input type="file"
                                            class="h-10 rounded mt-2 w-full flex" value=""
                                            placeholder="" />
                                    </div>

                                    <div class="md:col-span-5 text-left">
                                        <div class="inline-flex items-end">
                                            <button
                                                class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Qo'shish</button>
                                        </div>
                                    </div>

                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>