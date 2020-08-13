<template>
  <div class="sticky top-0 z-40 w-full h-16 bg-blue-600">
    <div class="container flex items-center justify-between w-full h-full">
      <!-- logo -->
      <a href="/" class="text-xl text-white focus:outline-none">
        <span class="font-bold">YM</span>SHOP
      </a>

      <!-- menu toggle -->
      <div
        class="p-1 text-gray-100 transition-colors duration-200 ease-out rounded cursor-pointer hover:bg-gray-700 hover:bg-opacity-25 hover:text-white"
        @click="showNavbar = true"
      >
        <div class="w-6 h-6">
          <svg fill="currentColor" viewBox="0 0 20 20">
            <path
              fill-rule="evenodd"
              d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM9 15a1 1 0 011-1h6a1 1 0 110 2h-6a1 1 0 01-1-1z"
              clip-rule="evenodd"
            />
          </svg>
        </div>
      </div>
    </div>

    <!-- menu -->
    <div
      class="absolute top-0 w-full transition duration-200 ease-in-out"
      :class="{
        'invisible opacity-0': !showNavbar,
        'visible opacity-100': showNavbar
      }"
    >
      <div class="mx-1 mt-1">
        <nav class="w-full bg-white rounded shadow">
          <div class="container w-full h-full">
            <!-- head -->
            <div class="flex items-center justify-between w-full h-12 pt-1">
              <!-- logo -->
              <a href="/" class="text-xl text-blue-600 focus:outline-none">
                <span class="font-bold">YM</span>SHOP
              </a>

              <!-- menu toggle -->
              <div
                class="p-1 text-blue-600 transition-colors duration-200 ease-out rounded cursor-pointer hover:bg-gray-400 hover:bg-opacity-25"
                @click="showNavbar = false"
              >
                <div class="w-6 h-6">
                  <svg fill="currentColor" viewBox="0 0 20 20">
                    <path
                      fill-rule="evenodd"
                      d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </div>
              </div>
            </div>

            <!-- menu_list -->
            <div class="flex flex-col w-full pt-3 pb-5 space-y-1">
              <n-link
                to="/daftarharga"
                class="px-4 py-2 transition-colors duration-200 rounded hover:bg-gray-300 hover:bg-opacity-25 focus:outline-none focus:bg-gray-300 focus:bg-opacity-25"
                active-class="text-white bg-blue-600 hover:bg-blue-600 hover:text-white hover:bg-opacity-100 focus:bg-blue-600 focus:bg-opacity-100"
                >Daftar Harga</n-link
              >
              <n-link
                to="/order"
                class="px-4 py-2 transition-colors duration-200 rounded hover:bg-gray-300 hover:bg-opacity-25 focus:outline-none focus:bg-gray-300 focus:bg-opacity-25"
                active-class="text-white bg-blue-600 hover:bg-blue-600 hover:text-white hover:bg-opacity-100 focus:bg-blue-600 focus:bg-opacity-100"
                >Order</n-link
              >
              <n-link
                to="/jualakun"
                class="px-4 py-2 transition-colors duration-200 rounded hover:bg-gray-300 hover:bg-opacity-25 focus:outline-none focus:bg-gray-300 focus:bg-opacity-25"
                active-class="text-white bg-blue-600 hover:bg-blue-600 hover:text-white hover:bg-opacity-100 focus:bg-blue-600 focus:bg-opacity-100"
                >Jual Akun</n-link
              >
            </div>
          </div>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "navbar.component",
  data() {
    return {
      showNavbar: false
    };
  }
};
</script>
