<template>
  <!-- Sidebar Navbar -->
<nav class="flex flex-col items-center bg-white min-h-screen p-4 space-y-4 w-20 sm:w-24">
  <!-- Home Button (Active) -->
  <a href="#"
    class="flex items-center justify-center bg-blue-600 text-white rounded-full w-14 h-14 shadow transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M3 9.75L12 3l9 6.75M4.5 10.5v9h15v-9" />
    </svg>
  </a>

  <!-- Other Buttons -->
  <a href="#"
    class="flex items-center justify-center bg-gray-100 text-gray-700 rounded-full w-12 h-12 hover:bg-gray-200 transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M12 14a4 4 0 100-8 4 4 0 000 8zm0 0v2a4 4 0 004 4H8a4 4 0 004-4v-2z" />
    </svg>
  </a>

  <a href="#"
    class="flex items-center justify-center bg-gray-100 text-gray-700 rounded-full w-12 h-12 hover:bg-gray-200 transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M9 12h6m2 0a2 2 0 002-2V6a2 2 0 00-2-2H7a2 2 0 00-2 2v4a2 2 0 002 2z" />
    </svg>
  </a>

  <a href="#"
    class="flex items-center justify-center bg-gray-100 text-gray-700 rounded-full w-12 h-12 hover:bg-gray-200 transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M15 10l4.553 2.276a1 1 0 01.447.724v.8a1 1 0 01-.447.724L15 17M9 10l-4.553 2.276A1 1 0 004 13v.8a1 1 0 00.447.724L9 17m6-7V7a2 2 0 00-2-2H11a2 2 0 00-2 2v3m6 0H9" />
    </svg>
  </a>

  <a href="#"
    class="flex items-center justify-center bg-gray-100 text-gray-700 rounded-full w-12 h-12 hover:bg-gray-200 transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M20 13V7a2 2 0 00-2-2H6a2 2 0 00-2 2v6m16 0v6a2 2 0 01-2 2H6a2 2 0 01-2-2v-6m16 0H4" />
    </svg>
  </a>

  <a href="#"
    class="flex items-center justify-center bg-gray-100 text-gray-700 rounded-full w-12 h-12 hover:bg-gray-200 transition duration-300 ease-in-out transform hover:scale-110">
    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
      stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
        d="M4 4h16v16H4V4zm4 4h8v8H8V8z" />
    </svg>
  </a>
</nav>

</template>

<script>
export default {
  name: 'Navbar'
}
</script>