<template>
  <div class="container mt-14 p-8">
    <form class="max-w-lg mx-auto mt-8 p-4 bg-slate-200 shadow-md rounded-md">
      <div class="text-center mb-4">
        <h1 class="text-2xl font-bold">GET IN TOUCH</h1>
      </div>
      <div class="mb-4">
        <label for="input-name" class="block text-sm font-medium text-gray-600"
          >Name</label
        >
        <input
          id="input-name"
          type="text"
          class="mt-1 p-2 w-full border rounded-md"
          required
        />
      </div>
      <div class="mb-4">
        <label for="input-email" class="block text-sm font-medium text-gray-600"
          >Email</label
        >
        <input
          id="input-email"
          type="email"
          class="mt-1 p-2 w-full border rounded-md"
          required
        />
      </div>
      <div class="mb-4">
        <label for="input-phone" class="block text-sm font-medium text-gray-600"
          >Phone Number</label
        >
        <input
          id="input-phone"
          type="number"
          class="mt-1 p-2 w-full border rounded-md"
          required
        />
      </div>
      <div class="mb-4">
        <label
          for="input-message"
          class="block text-sm font-medium text-gray-600"
          >Your Message</label
        >
        <textarea
          id="input-message"
          class="mt-1 p-2 w-full border rounded-md"
          cols="10"
          rows="5"
        ></textarea>
      </div>
      <div class="submit-contact">
        <button
          type="button"
          class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
          @click="submitData"
        >
          Submit
        </button>
      </div>
    </form>
  </div>
</template>

<script setup>
const submitData = () => {
  const name = document.getElementById("input-name").value;
  const email = document.getElementById("input-email").value;
  const phone = document.getElementById("input-phone").value;
  const message = document.getElementById("input-message").value;

  const mailtoURL = `mailto:angga.ardiansyah955@gmail.com?subject=Contact%20Form&body=Name:%20${name}%0AEmail:%20${email}%0APhone:%20${phone}%0AMessage:%20${message}`;

  window.location.href = mailtoURL;
};
</script>
