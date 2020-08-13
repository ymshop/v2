<template>
  <div class="w-full my-5 select-text">
    <div class="grid w-full grid-cols-2 gap-2 mb-3 select-none">
      <button
        class="px-6 py-3 uppercase transition-colors duration-200 border border-blue-600 rounded focus:outline-none hover:bg-blue-600 hover:text-white focus:bg-blue-600 focus:text-white"
        :class="
          harga
            ? 'text-white bg-blue-600'
            : 'text-blue-600 bg-transparent focus:bg-blue-600 focus:text-white'
        "
        @click="harga = true"
      >Harga Normal</button>
      <button
        class="px-6 py-3 uppercase transition-colors duration-200 border border-blue-600 rounded focus:outline-none hover:bg-blue-600 hover:text-white focus:bg-blue-600 focus:text-white"
        :class="
          !harga
            ? 'text-white bg-blue-600'
            : 'text-blue-600 bg-transparent focus:bg-blue-600 focus:text-white'
        "
        @click="harga = false"
      >Harga Pulsa</button>
    </div>
    <div class="grid w-full grid-cols-12 gap-2">
      <template v-if="harga">
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/aov.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/aov-load.png"
        />
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/codm.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/codm-load.png"
        />
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/ff.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/ff-load.png"
        />
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/ml.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/ml-load.png"
        />
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/pubgm.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/normal/pubgm-load.png"
        />
      </template>
      <template v-if="!harga">
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/pulsa/ff.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/pulsa/ff-load.png"
        />
        <v-lazy-image
          class="w-full col-span-12 rounded shadow-lg"
          src="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/pulsa/ml.png"
          src-placeholder="https://raw.githubusercontent.com/ymshop/v2/master/assets/img/pulsa/ml-load.png"
        />
      </template>
    </div>
  </div>
</template>

<script>
import VLazyImage from "v-lazy-image";

export default {
  name: "daftar-harga.page",
  components: {
    VLazyImage,
  },
  data() {
    return {
      harga: true,
    };
  },
  head() {
    return {
      title: "YMSHOP — Daftar Harga | Tempat Top Up Game Aman dan Cepat",
    };
  },
};
</script>

<style scoped></style>
