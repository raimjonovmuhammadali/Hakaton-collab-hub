<script>
import axios from 'axios';
import { projects } from '~/constants'

const route = useRoute();

const id = route.params.id

definePageMeta({
    layout: 'main',
});
useHead({
    title: 'Collab Hub | Details'
})


export default {

    data() {
        return {
            data: [],
        }
    },
    // async created() {
    //     const res = await axios.get('https://hakaton001.pythonanywhere.com/mainapp/project/' + route.params.id, {
    //         headers: {
    //             Authorization: 'Bearer ' + localStorage.getItem('token'),
    //         }
    //     })
    //     this.data = res.data
    //     console.log(this.data);
    // },
    created () {
            
            axios
                .get("https://hakaton001.pythonanywhere.com/mainapp/project/" + id + "/")
                .then((response) => {
                    console.log(response);
                    this.res = JSON.stringify(response.data);
                    this.data = response.data;
                })
                .catch((errors) => {
                    console.log(errors); // Errors
                });
        },

}

</script>
<template>
        <section class="flex items-center justify-center py-10 text-black">
            <div class="w-[85%]  shadow-md p-5 rounded-md flex justify-between gap-4">
                <iframe class="w-[50%] h-[400px]" src="https://www.youtube.com/embed/AFhI18hI3Xw"
                    title="No Copyright Video, Background, Green Screen, Motion Graphics, Animated Background, Copyright Free"
                    frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                <div class="w-[50%] flex flex-col gap-3">
                    <div class="flex flex-col gap-4">
                        <div>
                            <span class="text-xs font-semibold">{{ this.data.created_date }}</span>
                            <h1 class="text-xl font-semibold">{{ this.data.title }}
                            </h1>
                        </div>
                        <span class="text-md">Capital: ${{ this.data.price }}</span>
                    </div>
                    <p class="text-sm text-justify">{{ this.data.content }}</p>
                    <div class="flex justify-between my-4"><span class="flex items-center gap-1 font-semibold">
                            <Icon name="material-symbols:kid-star" v-for="i in 5" :color="i <= 5 ? 'orange' : 'gray'" />
                        </span>
                        <UButton color="primary" variant="outline">Sotildi</UButton>
                    </div>
                </div>

            </div>
        </section>
</template>