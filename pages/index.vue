<script>
// const isLogin = localStorage.getItem('isLogin')

import axios from "axios";
export default {
    data() {
        return {
            res: [],
        };
    },
        // The get method called by the function
        created () {
            
            axios
                .get("https://hakaton001.pythonanywhere.com/userapp/profile/", {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem('token'),
                    }
                })
                .then((response) => {
                    console.log(response);
                    this.res = JSON.stringify(response.data);
                    localStorage.setItem('userid', response.data.id);
                })
                .catch((errors) => {
                    console.log(errors); // Errors
                });
        },
};
</script>
<template>
    <main class="bg-white">
        <!-- OUR section -->
        <section class="w-full h-[75vh] pt-[10vh] bg-[#EBF5F3] relative">

            <div class="w-[85%] mx-auto flex items-center justify-between  gap-4 ">
                <div class="flex flex-col space-y-3 w-[45%] gap-3">
                    <h1 class="text-4xl font-bold text-[#181F38]">Hamkorlik qiling, g'oyalaringizni amalga oshiring, o'z ishingiz va jamoangizga ega bo'ling.</h1>
                    <p class="text-md opacity-80 text-[#181F38]">
                        - Start Up va g'oyalaringizni platformamiz orqali olib chiqing investorlar toping <br>
- Invetsitsiya qiling, o'z biznesingiz va daromadga ega bo'ling <br>
- O'z jamoangizni, ishingizni egallang <br>
                    </p>
                    <div class="flex gap-3">
                        <UButton color="primary" size="lg" v-if="isLogin"><span class="text-white">Kirish</span></UButton>
                        <UButton color="primary" size="lg" v-if="!isLogin" to="/inavator/home"><span class="text-white">Loyiha qo'shish</span></UButton>
                    </div>
                </div>
                <NuxtImg src="/img1.png" width="500px" />
            </div>
            <svg viewBox="0 0 1440 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="mt-10 rotate-180">
                <path
                    d="M0 43.9999C106.667 43.9999 213.333 7.99994 320 7.99994C426.667 7.99994 533.333 43.9999 640 43.9999C746.667 43.9999 853.333 7.99994 960 7.99994C1066.67 7.99994 1173.33 43.9999 1280 43.9999C1386.67 43.9999 1440 19.0266 1440 9.01329V100H0V43.9999Z"
                    class="fill-current text-[#EBF5F3]"></path>
            </svg>
        </section>

        <!-- ABOUT section -->
        <section class="w-[85%] mx-auto flex flex-col items-center justify-center  gap-4 py-10 my-10">
            <h1 class="text-3xl font-bold text-[#181F38]">Barchasi bizning <span class="text-green-500">platformada</span></h1>
            <p class="text-lg opacity-80 text-[#181F38] text-center w-[70%]">Bir platformada turib startuplar egasi, tadbirkor, freelancerga aylaning!</p>
            <div class="flex items-center justify-between">
                <div class="flex flex-col gap-5 w-[30%]">
                    <h1 class="text-3xl font-bold text-[#181F38]">G'oyalaringizni <br> amalga <span class="text-green-500">oshiring</span></h1>
                    <p class="text-lg opacity-80 text-[#181F38]">Rivojlanib borayotgan yosh zamonaviy soha vakillari uchun o’z ustida ishlash va shu soha bo’yicha o’zini o’zi band qilishni ta’minlash</p>
                    <p class="text-lg opacity-80 text-[#181F38]">Start Up va g’oya egalari & Investor tadbirkorlar o’rtasida ko’prik quruvchi platformani yaratish. Shuningdek ushbu jarayon bilan zamonaviy kasb egalari freelancelarni ish bilan taminlash!
                    </p>
                    <UButton color="primary" size="lg" class="w-[150px]"><span class="text-white">Ro'yhatdan o'tish</span></UButton>
                </div>
                <NuxtImg src="/img1.png" width="550px" class="shadow-lg p-5 rounded-md" />
            </div>
        </section>

        <!-- section -->
        <section class="w-full pt-[10vh] bg-[#EBEDF5] relative flex items-center justify-center flex-col mt-10 py-10">
            <svg viewBox="0 0 1440 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="absolute top-[-50px]">
                <path
                    d="M0 43.9999C106.667 43.9999 213.333 7.99994 320 7.99994C426.667 7.99994 533.333 43.9999 640 43.9999C746.667 43.9999 853.333 7.99994 960 7.99994C1066.67 7.99994 1173.33 43.9999 1280 43.9999C1386.67 43.9999 1440 19.0266 1440 9.01329V100H0V43.9999Z"
                    class="fill-current text-[#EBEDF5]"></path>
            </svg>
            <h1 class="text-3xl font-bold text-[#181F38]">O'z jamoangizga ega bo'ling</h1>
            <p class="text-lg opacity-80 text-[#181F38] text-center w-[70%]">Platformamizda startuplar orqali yaratilgan ish o'rinlari bo'yicha  o'zingizni band qiling</p>
            <div class="w-[85%] mx-auto flex flex-col items-center justify-center text-black">

                <div class="mt-10 flex gap-8">
                    <UButton color="primary" class="px-5 py-3"><span class="text-white text-xl">Ro'yhatdan o'tish</span></UButton>
                    <UButton color="primary" size="lg" variant="link" class="group text-xl hover" to="/startups"><span
                            class="text-green-800">Barcha loyihalar
                            <Icon name="quill:arrow-right" size="20"
                                class="group-hover:translate-x-2 ease-in-out duration-200" />
                        </span></UButton>
                </div>
            </div>

        </section>
    </main>
</template>