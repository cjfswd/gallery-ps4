<script setup lang="ts">
import { ref, onMounted, nextTick } from 'vue'

defineProps<{ fileName?: string, link: string }>()
</script>
<template>
    <NuxtLink :to="`/${link}`"
        class="nuxt-link rounded-lg shadow-lg border hover:shadow-xl shadow-blue-500/50 hover:shadow-blue-500/50">
        <p class="text">Loading...</p>
        <img
            class="lazyload w-full rounded-lg ring-1 ring-slate-500 hover:ring-blue-500 cursor-pointer"
            :data-src="fileName" :alt="fileName" />
    </NuxtLink>
</template>
<style scoped>
.nuxt-link {
    background-color: #003791;
    position: relative;
    width: 100%;
    padding-top: 108.1%;
    z-index: 1;
}

.text {
    position: absolute;
    top: calc(50% - 12px);
    left: 0;
    bottom: 0;
    right: 0;
    text-align: center;
    font-size: 20px;
    color: white;
    font-size: 12px;
}

img {
    position: absolute;
    top: 0;
}
</style>
