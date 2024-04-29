<script>
import axios from 'axios';


definePageMeta({
    layout: 'main',
});
// useHead({
//     title: 'Collab Hub | Home'
// })

const isLogin = localStorage.getItem('isLogin')
const userid = localStorage.getItem('userid')

const router = useRouter()

if (!isLogin) {
    router.push('/')
}

export default {
    data() {
        return {
            data: []
        }
    },
    async created() {
        const rest = await axios.get('https://hakaton001.pythonanywhere.com/mainapp/projects/', {
            headers: {
                Authorization: 'Bearer ' + localStorage.getItem('token'),
            }
        })

        this.data = rest.data
        console.log(rest.data);
    },
};

</script>
<template>
    <main class="bg-white">
        <!-- OUR section -->
        <section class="w-full h-[75vh] pt-[5vh] bg-[#EBF5F3] relative">

            <div class="w-[85%] mx-auto flex items-center justify-between  gap-4 bg-green-400 p-5 rounded-md">
                <div class="flex flex-col space-y-3 w-[40%] gap-3">
                    <h1 class="text-3xl font-bold">Hamkorlik qiling, g'oyalaringizni amalga oshiring, o'z ishingiz va jamoangizga ega bo'ling.</h1>
                    <p class="text-lg opacity-80">
                       - Start Up va g'oyalaringizni platformamiz orqali olib chiqing investorlar toping <br>
- Invetsitsiya qiling, o'z biznesingiz va daromadga ega bo'ling <br>
- O'z jamoangizni, ishingizni egallang <br>
                    </p>
                    <div class="flex gap-3">
                        <UButton color="black" size="lg" class="rounded-full" to="createproject"><span
                                class="text-black" to="/createproject">Loyiha qo'shish</span></UButton>
                    </div>
                </div>
                <NuxtImg src="/img1.png" width="500px" />
            </div>
        </section>

        <!-- Projects section -->
        <section class="w-[85%] mx-auto flex flex-col items-center justify-between  gap-4  p-5 rounded-md mt-10">
            <h1 class="text-4xl font-semibold text-black my-4">Mening <span class="text-green-400">loyihalarim</span>
            </h1>
            <div class="w-full flex items-center justify-between flex-wrap gap-4">
                <div v-for="(item, index) in this.data" :key="index"
                    class="w-[49%] flex flex-col justify-center gap-5 p-5 shadow-md rounded-lg bg-white text-black">
                    <div class="flex flex-col">
                        <span class="text-xs font-semibold">{{ item.created_date.split('T')[0] }}</span>
                        <NuxtLink :to='"/details/" + item.id'>
                            <h1 class="font-semibold text-xl text-green-700">{{item.title}}</h1>
                        </NuxtLink>
                    </div>
                    <span class="text-xs">Capital: ${{item.price}}</span>
                    <p class="text-sm">{{ item.desc }}</p>
                </div>
            </div>
        </section>
    </main>
</template>