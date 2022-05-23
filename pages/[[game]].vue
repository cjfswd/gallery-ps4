<script setup lang="ts">
import { computed } from "vue";
import cache from "../public/cache.json";

const route = useRoute();

const path = computed(() => route.path.replace("/", ""));

let images = cache.filter((item) => item.name == path.value)[0].images.filter((item) => !item.includes(".png"));
</script>

<template>
  <div class="w-full">
    <p class="m-2 md:m-3">
      {{ path.replace(/-/g, " ") }}
    </p>
    <div
      :class="'grid sm:grid-cols-2 md:grid-cols-2 xl:grid-cols-3 gap-2 md:gap-3 m-2 md:m-3'"
    >
      <div
        v-for="(image, index) in images"
        :key="index"
        class="image-wrapper rounded-lg shadow-lg hover:shadow-xl shadow-blue-500/50 hover:shadow-blue-500/50"
      >
        <p class="text">Loading...</p>
        <AtomPhoto :file-name="image" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.image-wrapper {
  background-color: #003791;
  position: relative;
  width: 100%;
  padding-top: 56.248383592820566%;
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
