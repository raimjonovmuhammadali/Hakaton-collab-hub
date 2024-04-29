<script>
definePageMeta({
    layout: 'main',
});
useHead({
    title: 'Collab Hub | Profile'
})



import axios from 'axios';

export default {

    data() {
        return {
            data: []
        }
    },
    async created() {
        const res = await axios.get('https://hakaton001.pythonanywhere.com/userapp/profil/' + localStorage.getItem('userid'), {
            headers: {
                Authorization: 'Bearer ' + localStorage.getItem('token'),
            }
        })

        this.data = res.data

    },
};

</script>
<template>
    <div class="w-[100%] shadow-md flex mx-auto">
        <div class="bg-gray-100">
            <div class="w-[85%] container mx-auto py-8">
                <div class="grid grid-cols-4 sm:grid-cols-12 gap-6 px-4">
                    <div class="col-span-4 sm:col-span-3">
                        <div class="bg-white shadow rounded-lg p-6">
                            <div class="flex flex-col items-center">
                                <img :src="this.data.profil_image"
                                    class="w-32 h-32 bg-gray-300 rounded-full mb-4 shrink-0">

                                </img>
                                <h1 class="text-xl font-bold text-black">{{ this.data.first_name }} {{
                                    this.data.last_name }}</h1>
                                <p class="text-gray-700">{{ this.data.job_title }}</p>
                                <div class="mt-6 flex flex-wrap gap-4 justify-center">
                                    <a :href="'tel:' + this.data.phone_number"
                                        class="bg-blue-500 hover:bg-blue-600 text-white py-2 px-4 rounded">Bog'lanish</a>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-span-4 sm:col-span-9">
                        <div class="bg-white shadow rounded-lg p-6">
                            <h2 class="text-xl font-bold mb-4 text-black">Biz haqimizda</h2>
                            <p class="text-gray-700">Languages & Frameworks & Technologies
Python, Django, Django Rest Framework, Channels, PostgreSQL, Flask, HTML, CSS, JavaScript
Other
GitHub, WebSocket, jwt-Token, Swagger, Redis, Deployment, django-multilanguage
pgAdmin, Insomnia, Postman ...
English: Pre-Intermedite (hozir. Registon LC.)
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>