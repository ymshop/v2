<template>
  <div class="fixed top-0 left-0 z-50 w-full h-full text-gray-900 bg-white">
    <div
      class="container flex flex-col items-center justify-center w-full h-full space-y-2"
    >
      <h1 class="text-6xl font-light">Ups!!</h1>
      <span class="text-2xl font-hairline">Halaman Tidak Ditemukan</span>
      <div class="pt-5">
        <a
          href="/"
          class="px-4 py-2 text-white transition-colors duration-200 bg-blue-600 rounded hover:bg-blue-700"
          >Halaman Utama</a
        >
      </div>
    </div>
    <a
      class="absolute z-50 transition-colors duration-200 hover:text-blue-600"
      style="bottom: 15px; right: 15px;"
      href="https://instagram.com/ymshop28"
      target="_blank"
      >@ymshop28</a
    >
  </div>
</template>

<script>
export default {
  name: "error.layout",
  mounted() {
    document.title = "YMSHOP | Halaman Tidak Ditemukan";
  }
};
</script>
