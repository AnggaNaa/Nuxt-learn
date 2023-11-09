<template>
  <div class="flex flex-col gap-4">
    <div class="container-img"><img src="../assets/image4.jpg" alt="" /></div>
    <div class="mx-auto my-8 flex gap-5">
      <div
        v-for="item in data"
        :key="item.id"
        class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:border-gray-700 text-ellipsis whitespace-nowrap overflow-hidden"
      >
        <img class="rounded-t-lg" :src="item.image" alt="" />
        <div class="p-3">
          <nuxt-link :to="'/detail/' + item.id">
            <h5 class="mb-2 text-2xl font-bold tracking-tight">
              {{ item.title }}
            </h5>
          </nuxt-link>

          <p class="mb-3 font-normal dark:text-gray-400">
            {{ item.detail }}
          </p>
        </div>
      </div>
    </div>
    <div class="w-1/2 mx-auto my-6 text-center">
      <h1 class="text-4xl font-bold mb-4" id="about">About Us</h1>
      <p>
        Welcome to our website! We are a team of passionate individuals
        dedicated to creating amazing things. Lorem ipsum dolor sit amet,
        consectetur adipiscing elit. Nullam non metus ac elit ultricies suscipit
        vel vel libero.
      </p>
    </div>
  </div>
</template>

<style>
.container-img img {
  width: 100%;
  height: 600px;
}

.card-img {
  text-overflow: ellipsisw;
}

.card-img img {
  width: 100%;
  height: 85%;
  border-radius: 10px 10px 0 0;
  overflow: hidden;
}
</style>

<script>
import dataDummy from "~/utils/dataDummy.json";

const data = dataDummy;

export default {
  data() {
    return {
      data,
    };
  },
};
</script>
