<template>
  <div class="mx-auto mt-24 w-1/3">
    <form
      @submit.prevent="handleSubmit"
      class="bg-slate-200 shadow-md rounded px-8 pt-6 pb-8 mb-4"
    >
      <div class="flex flex-col gap-5">
        <label for="namaKapal" class="text-sm font-bold text-gray-600"
          >Nama Kapal</label
        >
        <input
          v-model="formData.namaKapal"
          type="text"
          name="namaKapal"
          placeholder="Nama Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
          required
        />

        <label for="asalKapal" class="text-sm font-bold text-gray-600"
          >Asal Kapal</label
        >
        <input
          v-model="formData.asalKapal"
          type="text"
          name="asalKapal"
          placeholder="Asal Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
          required
        />

        <label for="tujuanKapal" class="text-sm font-bold text-gray-600"
          >Tujuan Kapal</label
        >
        <input
          v-model="formData.tujuanKapal"
          type="text"
          name="tujuanKapal"
          placeholder="Tujuan Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
          required
        />

        <label for="muatanKapal" class="text-sm font-bold text-gray-600"
          >Muatan Kapal</label
        >
        <input
          v-model="formData.muatanKapal"
          type="text"
          name="muatanKapal"
          placeholder="Muatan Kapal"
          class="py-2 px-3 border border-gray-300 rounded focus:outline-none focus:shadow-outline-blue focus:border-blue-500"
          required
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
  <div class="w-2/3 mx-auto my-8">
    <table v-if="savedData.length > 0" class="saved-data-table">
      <thead>
        <tr>
          <th class="text-left">Nama Kapal</th>
          <th class="text-left">Asal Kapal</th>
          <th class="text-left">Tujuan Kapal</th>
          <th class="text-left">Muatan Kapal</th>
          <th class="text-left">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in savedData" :key="index">
          <td>{{ data.namaKapal }}</td>
          <td>{{ data.asalKapal }}</td>
          <td>{{ data.tujuanKapal }}</td>
          <td>{{ data.muatanKapal }}</td>
          <td class="flex justify-center">
            <button @click="editData(index)" class="edit-button">Edit</button>
            <button @click="deleteData(index)" class="delete-button">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        namaKapal: "",
        asalKapal: "",
        tujuanKapal: "",
        muatanKapal: "",
      },
      savedData: [],
      editingIndex: null,
    };
  },

  methods: {
    handleSubmit() {
      if (this.editingIndex !== null) {
        // Update existing data
        this.savedData[this.editingIndex] = { ...this.formData };
        this.editingIndex = null;
      } else {
        // Save new data
        this.savedData.push({ ...this.formData });
      }

      // Save to local storage
      localStorage.setItem("kapalData", JSON.stringify(this.savedData));

      // Clear form fields
      this.formData = {
        namaKapal: "",
        asalKapal: "",
        tujuanKapal: "",
        muatanKapal: "",
      };
    },
    editData(index) {
      // Populate form with data for editing
      this.formData = { ...this.savedData[index] };
      this.editingIndex = index;
    },
    deleteData(index) {
      // Delete data and save to local storage
      this.savedData.splice(index, 1);
      localStorage.setItem("kapalData", JSON.stringify(this.savedData));
    },
  },
  mounted() {
    // Retrieve data from local storage on component mount
    const storedData = localStorage.getItem("dataKapal");
    if (storedData) {
      this.savedData = JSON.parse(storedData);
    }
  },
};
</script>

<style scoped>
.saved-data-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 1.5rem;
}

.saved-data-table th,
.saved-data-table td {
  border: 1px solid #e2e8f0;
  padding: 0.75rem;
  text-align: left;
}

.saved-data-table th {
  background-color: #edf2f7;
}

.saved-data-table tr:hover {
  background-color: #f7fafc;
}

.edit-button {
  background-color: #3182ce;
  color: #ffff;
  padding: 0.25rem 1.2rem;
  border-radius: 0.25rem;
}
.delete-button {
  cursor: pointer;
  color: #3182ce;
  margin-left: 0.5rem;
}

.delete-button {
  background-color: #e53e3e;
  color: #ffff;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
}
</style>
