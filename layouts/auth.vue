<script setup lang="ts">
import { useLoadingStore } from '~/store/loading.store';


const loadingStore = useLoadingStore()

setTimeout(() => {
    loadingStore.set(false)
}, 3000);
</script>
<template>
    <UiLoader v-if="loadingStore.isLoading" />

    <template v-else>
        <LayoutNavbar/>
    <section class="bg-white">
        <slot />
    </section>
    </template>
</template>