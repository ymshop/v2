<template>
  <div
    class="flex flex-col items-center justify-center w-full h-full space-y-2 text-gray-900 select-text"
  >
    <h1 class="text-4xl font-light">
      <span class="font-bold text-blue-600">YM</span>SHOP
    </h1>
    <p class="px-5 text-center">
      Sebuah Tempat Untuk Kalian Para
      <span class="font-medium">Gamers</span> Yang Ingin
      <span class="font-medium">Top Up</span> Dengan Aman, Cepat Dan Murah
    </p>
    <div class="flex w-full pt-5 space-x-2">
      <n-link
        to="/daftar-harga"
        class="w-full py-3 text-center text-white transition-colors duration-200 bg-blue-600 border border-blue-600 rounded hover:bg-blue-600 hover:text-white"
      >Daftar Harga</n-link>
      <n-link
        to="/order"
        class="w-full py-3 text-center text-blue-600 transition-colors duration-200 border border-blue-600 rounded hover:bg-blue-600 hover:text-white"
      >Order</n-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "index.page",
};
</script>
