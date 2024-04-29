<script>
import axios from 'axios';

useHead({ 'title': 'Collab Hub | Startups' })
export default {

    data() {
        return {
            data: [],
            category: [],
            profile: [],
            userid: '',
        }
    },
    async created() {
        const res = await axios.get('https://hakaton001.pythonanywhere.com/connectapp/vacancies/')

        this.data = res.data
        const ress = await axios.get('https://hakaton001.pythonanywhere.com/mainapp/category/')
        this.category = ress.data
        
        const profile = await axios.get('https://hakaton001.pythonanywhere.com/userapp/profil/' + this.userid, {
            headers: {
                Authorization: 'Bearer ' + localStorage.getItem('token'),
            }
        })
        this.profile = profile.data
    },
};
</script>
<template>
    <main class="bg-white">
        <!-- OUR section -->
        <section class="w-full h-[75vh] pt-[5vh] bg-[#EBF5F3] relative">

            <div class="w-[85%] mx-auto flex items-center justify-between  gap-4 rounded-md">
                <NuxtImg src="img4.jpg" class="w-full h-[450px] rounded-md"/>
            </div>
        </section>

        <!-- Projects section -->
        <section class="w-[85%] mx-auto flex flex-col items-center justify-between  gap-4  p-5 rounded-md mt-10">
            <div class="w-full flex items-center justify-between">
                <h1 class="text-4xl font-semibold text-black my-4">Ish <span class="text-green-400">o'rinlari</span></h1>
                <div class="flex gap-3">
                    <select name="" id="" class="px-4 py-2 bg-white text-black outline-none border-b-2 border-b-green-500">
                    <option value="all" selected>Barchasi</option>
                    <option value="" v-for="(item, index) in this.category" :key="index">{{ item.name }}</option>
                </select>
                <select name="" id="" class="px-4 py-2 bg-white text-black outline-none border-b-2 border-b-green-500">
                    <option value="">Saralash</option>
                    <option value="">Reyting bo'yicha</option>
                    <option value="">Eng arzoni</option>
                    <option value="">Eng qimmati</option>
                </select>
                </div>
            </div>
            <div class="w-full flex items-center justify-between flex-wrap gap-4 text-black">
                <div v-for="(item, index) in this.data" :key="index"
                    class="w-[49%] flex flex-col justify-center gap-5 p-5 shadow-md rounded-lg bg-white text-black">
                    <div class="flex flex-col">
                        <span class="text-xs font-semibold">{{ item.created_date.split('T')[0] }}</span>
                        <NuxtLink :to='"/details/" + item.id'>
                            <h1 class="font-semibold text-xl text-green-700">{{ item.title }} <span class="hidden">{{ userid = item.user }}</span>{{ userid }}</h1>
                        </NuxtLink>
                    </div>
                    <p class="text-sm">{{ item.description }}</p>
                    <hr>
                    <div class="flex items-center justify-between">
                        <div>
                            <UButton>Bog'lanish</UButton>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>