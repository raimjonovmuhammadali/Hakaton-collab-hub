<script setup lang="ts">
import { projects } from '~/constants'

</script>

<template>
    <div v-for="(item, index) in projects" :key="index"
        class="w-[49%] flex flex-col justify-center gap-5 p-5 shadow-md rounded-lg bg-white text-black">
        <div class="flex flex-col">
            <span class="text-xs font-semibold">Posted 5 hours ago</span>
            <NuxtLink :to='"/details/" + item.id'>
                <h1 class="font-semibold text-xl text-green-700">Lorem, ipsum dolor sit amet consectetur adipisicing
                    elit.</h1>
            </NuxtLink>
        </div>
        <span class="text-xs">Capital: $1000</span>
        <p class="text-sm">{{ item.desc }}</p>
        <div class="flex justify-between my-4"><span class="flex items-center gap-1 font-semibold">
            <Icon name="material-symbols:kid-star" v-for="i in 5"
                                :color="i <= item.rating ? 'orange' : 'gray'" />
            </span>
            <UButton color="primary" variant="ghost">Sotildi</UButton>
        </div>
    </div>
</template>