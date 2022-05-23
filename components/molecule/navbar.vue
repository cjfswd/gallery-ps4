<script setup lang="ts">
import { computed } from 'vue'

const route = useRoute();

const path = computed(() => route.path)
</script>

<template>
    <nav class="center-x space-between bg-primary-color shadow-lg shadow-blue-500/50 w-100 px-2 md:px-3">
        <div class="flex items-center justify-between gap-4">
            <NuxtLink to="/" style="height: 64px;display: flex;">
                <img v-if="path != '/'" data-src="/icon/arrow-left.svg" class="lazyload"
                    style="width: 24px; filter: invert(15%) sepia(95%) saturate(1894%) hue-rotate(206deg) brightness(98%) contrast(110%);" />
            </NuxtLink>
            <NuxtLink to="/" class="flex items-center justify-center gap-4">
                <span style="height: min-content; display: block; margin-bottom: -1px; font-size: 13px;">PS4 Photo
                    Project</span>
            </NuxtLink>
            <NuxtLink to="/about" style="height: 64px;display: flex;">
                <img v-if="path != 'about'" data-src="/icon/information.svg" class="lazyload"
                    style="width: 24px; filter: invert(15%) sepia(95%) saturate(1894%) hue-rotate(206deg) brightness(98%) contrast(110%);" />
            </NuxtLink>
        </div>
    </nav>
</template>

<style scoped>
nav {
    height: 64px;
}

a {
    color: inherit;
    cursor: pointer;
    text-decoration: none;
}
</style>
