<script setup lang="ts">

const items = [
    [{
        label: 'Profile',
    }], [{
        label: 'Edit',
        click: () => {
            console.log('Edit')
        }
    }, {
        label: 'Duplicate',
    }], [{
        label: 'Archive',
    }, {
        label: 'Move',
    }], [{
        label: 'Delete',
    }]
]

const isLogin = localStorage.getItem('isLogin')
const userid = localStorage.getItem('userid')

const router = useRouter();

function logout (){
    localStorage.removeItem('isLogin');
    localStorage.removeItem('token');
    localStorage.removeItem('userid');
    router.push('/login')
}

</script>
<template>
    <div class="w-full h-[10vh] flex top-0 left-0 right-0 z-50 items-center justify-center bg-[#EBF5F3] text-black">
        <div class="w-[85%] mx-auto">
            <div class="flex gap-10 items-center justify-between">
                <div class="flex items-center gap-10">
                    <NuxtLink to="/">
                        <h1 class="text-2xl font-bold">Collab Hub</h1>
                    </NuxtLink>
                    <div class="flex gap-3 items-center">
                        <nuxt-link to="/startups/" class="text-md">StartUplar</nuxt-link>
                        <nuxt-link to="/auction/" class="text-md">Auksionlar</nuxt-link>
                        <nuxt-link to="/vacancy" class="text-md">Ish o'rinlari</nuxt-link>
                        <nuxt-link to="/about/" class="text-md">Biz haqimizda</nuxt-link>
                    </div>
                </div>
                <div class="flex items-center gap-8">
                    <NuxtLink to="/login" class="text-green font-semibold text-base" v-if="!isLogin">Kirish</NuxtLink>
                    <UButton color="primary" size="md" to="/login" v-if="!isLogin"><span class="text-white text-base">Ro'yhatdan o'tish</span></UButton>
                    <NuxtLink :to="'/profile/' + userid" class="text-green font-semibold text-base" v-if="isLogin">Profil</NuxtLink>
                    <UButton @click="logout" v-if="isLogin">Chiqish</UButton>
                </div>
            </div>
        </div>
    </div>
</template>