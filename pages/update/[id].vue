<template>
  <div class="mx-auto my-10 w-1/3">
    <form action="" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="flex flex-col gap-5">
        <label for="namaKapal" class="text-sm font-bold text-gray-600"
          >Nama Kapal</label
        >
        <input
          type="text"
          name="namaKapal"
          placeholder="Nama Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
        />

        <label for="asalKapal" class="text-sm font-bold text-gray-600"
          >Asal Kapal</label
        >
        <input
          type="text"
          name="asalKapal"
          placeholder="Asal Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
        />

        <label for="tujuanKapal" class="text-sm font-bold text-gray-600"
          >Tujuan Kapal</label
        >
        <input
          type="text"
          name="tujuanKapal"
          placeholder="Tujuan Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
        />

        <label for="muatanKapal" class="text-sm font-bold text-gray-600"
          >Muatan Kapal</label
        >
        <input
          type="text"
          name="muatanKapal"
          placeholder="Muatan Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
        />
        <div class="flex justify-between">
          <nuxt-link to="/">
            <button class="bg-red-500 text-white font-bold py-2 px-4 rounded">
              Cancel
            </button>
          </nuxt-link>
          <button
            type="submit"
            class="bg-blue-500 text-white font-bold py-2 px-4 rounded"
          >
            Submit
          </button>
        </div>
      </div>
    </form>
  </div>
</template>
<script setup lang="ts">
const route = useRoute();
console.log(route.params.id);
</script>
