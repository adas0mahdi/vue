<script setup>
import { ref } from 'vue';

const reviews = ref([
  { source: 'Trustpilot', rating: 4.2, reviews: '45k Reviews', stars: 5 },
  { source: 'Capterra', rating: 4.1, reviews: '18k Reviews', stars: 4 }
]);

const menuOpen = ref(false);
</script>

<template>
  <div class="min-h-screen flex flex-col roboto-regular">
    <div class="flex justify-center">
      <header class="bg-white shadow-md rounded-[50px] w-[90%] mt-6">
        <div class="container mx-auto flex justify-between items-center px-6 py-2">
          <img src="/logo.png" alt="Zanrly" class="w-[60px]">
          <nav :class="{ 'translate-x-0': menuOpen, '-translate-x-full': !menuOpen }" class="fixed inset-y-0 left-0 z-30 w-64 bg-white shadow-lg transform transition-transform duration-300 md:static md:w-auto md:shadow-none md:transform-none md:flex md:items-center md:space-x-6">
            <div class="flex justify-between items-center p-4 md:hidden">
              <h2 class="text-lg font-semibold text-gray-800">Menu</h2>
              <button @click="menuOpen = !menuOpen" class="text-gray-800 hover:text-blue-600">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
            <a href="#" class="block px-4 py-2 text-gray-800 hover:text-blue-600">Features</a>
            <a href="#" class="block px-4 py-2 text-gray-800 hover:text-blue-600">Solutions</a>
            <a href="#" class="block px-4 py-2 text-gray-800 hover:text-blue-600">Resources</a>
            <a href="#" class="block px-4 py-2 text-gray-800 hover:text-blue-600">Pricing</a>
          </nav>
          <div class="hidden md:flex items-center space-x-4">
            <button class="text-gray-800 hover:text-blue-600">Log In</button>
            <button class="bg-blue-600 text-white px-4 py-2 rounded-md hover:bg-blue-700">Get Started</button>
          </div>
          <button @click="menuOpen = !menuOpen" class="block md:hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
            </svg>
          </button>
        </div>
      </header>
    </div>

    <main class="flex-1">
      <section class="container mx-auto p-6 grid grid-cols-1 md:grid-cols-12 gap-6 items-center">
        <div class="md:col-span-4 md:col-start-2">
          <p class="text-blue-600 font-semibold roboto-regular">Best Caption Here</p>
          <h1 class="text-4xl font-bold mt-2 roboto-regular">Build online business from home.</h1>
          <p class="text-gray-600 mt-4 roboto-light">Amet minim mollit non deserunt ullamco est sit aliqua dolor do amet sint. Velit officia consequat duis enim velit mollit. Exercitation veniam consequat.</p>
          <div class="mt-6 flex space-x-4">
            <button class="bg-blue-600 text-white px-4 py-2 rounded-md hover:bg-blue-700 roboto-regular">Get Started</button>
            <button class="border border-blue-600 text-blue-600 px-4 py-2 rounded-md hover:bg-blue-600 hover:text-white roboto-regular">Watch Video</button>
          </div>
        </div>
        <div class="md:col-span-6 md:col-start-8 flex justify-center">
          <img src="../assets/img/one.png" alt="Smiling woman" class="rounded-md">
        </div>
      </section>
      
      <section class="container w-full mx-auto p-6">
        <div class="flex space-x-4 overflow-x-auto mx-[1px] md:mx-[115px]">
          <div v-for="review in reviews" :key="review.source" class="bg-white shadow-md rounded-md p-4 min-w-[300px]">
            <div class="flex items-center space-x-2">
              <img :src="`src/assets/img/${review.source}.png`" :alt="review.source" class="w-8">
              <div>
                <p class="text-gray-800 font-semibold">{{ review.source }}</p>
                <p class="text-gray-600">{{ review.reviews }}</p>
              </div>
            </div>
            <div class="flex items-center mt-2">
              <div class="flex space-x-1">
                <span v-for="i in review.stars" :key="i" class="text-yellow-500">★</span>
              </div>
              <p class="text-gray-800 ml-2">{{ review.rating }}/5</p>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400&display=swap');

.roboto-light {
  font-family: "Roboto", sans-serif;
  font-weight: 300;
  font-style: normal;
}

.roboto-regular {
  font-family: "Roboto", sans-serif;
  font-weight: 400;
  font-style: normal;
}

:root {
  --font-family: 'Roboto', sans-serif;
  --font-weight: 400;
  --font-size: 16px;
  --color-primary: #1D4ED8;
  --color-secondary: #3B82F6;
  --color-accent: #FBBF24;
  --color-bg: #F3F4F6;
  --color-text: #1F2937;
}

body {
  font-family: var(--font-family);
  font-weight: var(--font-weight);
  font-size: var(--font-size);
  background-color: var(--color-bg);
  color: var(--color-text);
}
</style>
