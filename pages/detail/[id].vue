<template>
  <div>
    <template>
      <div class="container mx-auto mt-24 p-8">
        <div class="max-w-2xl mx-auto">
          <img
            v-if="item"
            :src="item.image"
            alt="Image"
            class="w-full h-64 object-cover rounded-md mb-6"
          />

          <h1 class="text-3xl font-bold mb-4" v-if="item">{{ item.title }}</h1>
          <div
            v-if="item"
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
const item = ref(null);

const fetchData = async () => {
  const itemId = route.params.id;
  const result = dataDummy.find((item) => item.id == itemId);

  if (result) {
    item.value = result;
  } else {
    // Handle case when item is not found
    console.error("Item not found");
  }
};

onMounted(() => {
  fetchData();
});

// import dataDummy from "../utils/dataDummy.json";
// import { useRoute } from "vue-router";

// const route = useRoute();

// const item = dataDummy.find((item) => item.id == route.params.id);
</script>
