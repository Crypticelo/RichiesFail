<template>
  <nav class="bg-blue-600 text-white">
    <div class="max-w-6xl mx-auto px-4">
      <div class="flex justify-between">
        <div class="flex space-x-4">
          <div>
            <a href="/" class="flex items-center py-5 px-2 text-white">
              <span class="font-bold text-xl">Richies Epic Fail</span>
            </a>
          </div>
          <div class="hidden md:flex items-center space-x-1">
            <a href="/" class="py-5 px-3 hover:bg-gray-700">Home</a>
            <a href="/about" class="py-5 px-3 hover:bg-gray-700"
              >About Richie</a
            >
            <a href="/difficulties" class="py-5 px-3 hover:bg-gray-700"
              >His Difficulties</a
            >
          </div>
        </div>
        <div class="md:hidden flex items-center">
          <button class="mobile-menu-button">
            <svg
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16m-7 6h7"
              ></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
    <div class="mobile-menu hidden md:hidden">
      <a href="/" class="block py-2 px-4 text-sm hover:bg-gray-700">Home</a>
      <a href="/about" class="block py-2 px-4 text-sm hover:bg-gray-700"
        >About Richie</a
      >
      <a href="/difficulties" class="block py-2 px-4 text-sm hover:bg-gray-700"
        >His Difficulties</a
      >
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
};
</script>
