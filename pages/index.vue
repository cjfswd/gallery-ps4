<script setup lang="ts">
import cache from "../public/cache.json";

const indexGameData = cache.map((item) => {
  return {
    name: item.name,
    fileName: item.images.filter((image) => image.includes(".png"))[0],
    link: "",
  };
});

const top5OrderFilter = [
  "god-of-war",
  "ghost-of-tshushima",
  "the-last-of-us-part-ii",
  "horizon-zero-dawn",
  "the-order-1886",
];

const othersOrderFilter = [
  "uncharted-4",
  "marvels-spider-man",
  "days-gone",
  "bloodborne",
  "infamous-second-son",
  "detroit-become-human",
  "until-dawn",
  "killzone-shadow-fall",
  "ratchet-clank",
  "concrete-genie",
];

const dlcOrderFilter = [
  "marvels-spider-man-miles-morales",
  "uncharted-lost-legacy",
  "horizon-zero-dawn-the-frozen-wilds",
  "infamous-first-light",
];

const racingOrderFilter = ["gran-turismo-sport", "driveclub"];

const remakeOrderFilter = ["final-fantasy-vii-remake", "shadow-of-the-colossus"];

type IGame = {
  name: string;
  fileName: string;
  link: string;
};

class GameList {
  data: IGame[];
  constructor(toOrderAndFilter: IGame[], gameOrderAndFilter: string[]) {
    this.filter(toOrderAndFilter, gameOrderAndFilter).orderByName(
      this.data,
      gameOrderAndFilter
    );
  }
  filter(toFilter: IGame[], filter: string[]) {
    this.data = toFilter.filter((item) => filter.includes(item.name));
    return this;
  }
  orderByName(toOrder: IGame[], order: string[]) {
    this.data = toOrder
      .map((mapItem) => {
        return {
          order: order.findIndex((filterItem) => filterItem == mapItem.name),
          ...mapItem,
        };
      })
      .sort((a, b) => (a.order > b.order ? 1 : -1));
    return this;
  }
}

const top5 = new GameList(indexGameData, top5OrderFilter);
const others = new GameList(indexGameData, othersOrderFilter);
const racing = new GameList(indexGameData, racingOrderFilter);
const remake = new GameList(indexGameData, remakeOrderFilter);
const dlc = new GameList(indexGameData, dlcOrderFilter);
</script>

<template>
  <div>
    <p class="m-2 md:m-3">Top 5</p>
    <div
      class="grid grid-cols-12 grid-rows-2 sm:grid-cols-4 sm:grid-rows-2 lg:grid-cols-5 lg:grid-rows-1 xl:grid-cols-8 gap-2 md:gap-3 m-2 md:m-3"
    >
      <AtomCover
        v-for="(x, index) in top5.data"
        :key="index"
        :class="
          index == 0
            ? 'col-start-4 col-span-6 row-span-2 sm:col-span-2 sm:row-span-2 lg:col-span-1 lg:row-span-1 w-full rounded-lg drop-shadow-lg cursor-pointer'
            : 'w-full col-span-6 row-span-2 sm:col-span-1 sm:row-span-1 rounded-lg drop-shadow-lg cursor-pointer'
        "
        :file-name="x.fileName"
        :link="x.name"
      />
    </div>
    <p class="mt-6 md:mt-6 m-2 md:m-3">Outros</p>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-8 gap-2 md:gap-3 m-2 md:m-3"
    >
      <AtomCover
        v-for="(x, index) in others.data"
        :key="index"
        :file-name="x.fileName"
        :link="x.name"
      />
    </div>
    <p class="mt-6 md:mt-6 m-2 md:m-3">DLC</p>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-8 gap-2 md:gap-3 m-2 md:m-3"
    >
      <AtomCover
        v-for="(x, index) in dlc.data"
        :key="index"
        :file-name="x.fileName"
        :link="x.name"
      />
    </div>
    <p class="mt-6 md:mt-6 m-2 md:m-3">Corrida</p>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-8 gap-2 md:gap-3 m-2 md:m-3"
    >
      <AtomCover
        v-for="(x, index) in racing.data"
        :key="index"
        :file-name="x.fileName"
        :link="x.name"
      />
    </div>
    <p class="mt-6 md:mt-6 m-2 md:m-3">Remake</p>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-8 gap-2 md:gap-3 m-2 md:m-3"
    >
      <AtomCover
        v-for="(x, index) in remake.data"
        :key="index"
        :file-name="x.fileName"
        :link="x.name"
      />
    </div>
  </div>
</template>

<style scoped>
label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
