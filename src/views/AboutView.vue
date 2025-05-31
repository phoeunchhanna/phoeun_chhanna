<template>
  <div class="max-w-2xl mx-auto space-y-8">
    <h1 class="text-3xl font-bold text-gray-800 mb-6">Tailwind CSS Shadows</h1>

    <!-- Shadow MD (medium) -->
    <div class="shadow-md shadow-blue-700 hover:shadow-2xl hover:shadow-red-600   p-6 bg-yellow-500 rounded-full">
      <h2 class="text-xl font-serif text-blue-900 hover:text-red-600 opacity-5 hover:opacity-100 md:bg-green-500">
        shadow-md</h2>
    </div>

    <!-- Shadow LG (large) -->
    <div class="shadow-lg shadow-red-400 p-6 bg-white  blur-md  rounded-lg mix-blend-multiply ">
      <h2 class="text-xl font-semibold text-gray-700 ">shadow-lg</h2>
      <p class="text-gray-600 mt-2 ">Large shadow - more pronounced elevation</p>
    </div>

    <!-- Shadow XL (extra large) -->
    <div class="shadow-xl p-6 bg-white rounded-lg hover:drop-shadow-xl">
      <h2 class="text-xl font-semibold text-gray-700">shadow-xl</h2>
      <p class="text-gray-600 mt-2">Extra large shadow - for significant elevation</p>
    </div>

    <!-- Shadow 2XL (2x extra large) -->
    <div class="shadow-2xl p-6 bg-white rounded-lg">
      <h2 class="text-xl font-semibold text-gray-700">shadow-2xl</h2>
      <p class="text-gray-600 mt-2">2X extra large shadow - maximum elevation</p>
    </div>
    <div>
      <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-sky-400 opacity-75"></span>
      <button
        class="transition transform hover:-translate-y-1 motion-reduce:transition-none motion-reduce:hover:transform-none ...">
        Hover me
      </button>
    </div>

  </div>
</template>
