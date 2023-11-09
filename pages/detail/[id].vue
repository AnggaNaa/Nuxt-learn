<template>
  <div>
    <template>
      <div class="container mx-auto p-8">
        <div class="max-w-2xl mx-auto">
          <img
            :src="item.image"
            alt="Image"
            class="w-full h-64 object-cover rounded-md mb-6"
          />

          <h1 class="text-3xl font-bold mb-4">{{ item.title }}</h1>
          <div
            v-html="item.detail"
            class="text-base text-gray-700 leading-relaxed mb-8"
          ></div>
        </div>
      </div>
    </template>
  </div>
</template>
<script setup>
import dataDummy from "../utils/dataDummy.json";
import { useRoute } from "vue-router";

const route = useRoute();

const item = dataDummy.find((item) => item.id == route.params.id);
</script>
