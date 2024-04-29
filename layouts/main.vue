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
        <LayoutNavbar />
        <section class="min-h-screen bg-white">
            <slot />
        </section>
        <LayoutFooter />
    </template>
</template>