<script setup lang="ts">
defineProps<{ fileName?: string }>()
</script>
<template>
    <img class="lazyload w-full rounded-lg ring-1 ring-slate-500 hover:ring-blue-500 cursor-pointer" loading="lazy"
        :data-src="fileName" :alt="fileName" :onclick="`window.open('${fileName}', '_blank')`" />
</template>
<style scoped>
.lazyload,
.lazyloading {
    opacity: 0;
}

.lazyloaded {
    opacity: 1;
    transition: opacity 300ms;
}

.relative {
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
    width: 100%;
    height: auto;
}
</style>
