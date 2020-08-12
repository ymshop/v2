<template>
  <div class="flex flex-col justify-center my-5 select-text">
    <h3
      class="flex flex-col space-y-3 text-lg font-normal leading-relaxed tracking-wide text-center"
    >
      <span>Kamu pengen jual akun game? Bingung mau posting dimana? Tenang kita punya solusinya.</span>
      <span>
        Ayo pakai jasa jual akun dari YMSHOP, akun anda akan kami posting di
        <a
          href="https://instagram.com/ymshop28"
          target="_blank"
          class="font-medium underline transition-colors duration-200 hover:text-blue-600"
        >Instagram</a> kami.
      </span>
      <span>
        Caranya gampang kok kamu tinggal isi aja data yang ada dibawah dan klik tombol
        <span
          class="px-2 py-1 text-sm text-white bg-blue-600 rounded"
        >kirim data</span>
      </span>
    </h3>
  </div>
</template>

<script>
export default {
  name: "jual-akun.page",
  data() {
    return {
      admins: {
        62895328311263: "Kirim Data",
      },
    };
  },

  computed: {
    pesan() {},
  },

  head() {
    return {
      title: "YMSHOP — Jual Akun | Tempat Top Up Game Aman dan Cepat",
    };
  },
  directives: {
    focus: {
      // directive definition
      inserted: function (el) {
        el.focus();
      },
    },
  },
};
</script>

<style scoped>
#select:focus + #arrow_select {
  color: #3182ce;
}
</style>
