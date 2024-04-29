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
        <hr>
        <div class="flex items-center justify-between">
            <div class="flex items-center gap-4">
                <NuxtLink to="/profile/1" class="flex items-center gap-4"><UAvatar size="sm" src="https://avatars.githubusercontent.com/u/739984?v=4" alt="Avatar" />
                <p>Abduvaliyev Salohiddin</p></NuxtLink>
            </div>
            <div>
                <Icon name="material-symbols:kid-star" v-for="i in 5" :color="i <= item.rating ? 'orange' : 'gray'" />
            </div>
        </div>
    </div>
</template>