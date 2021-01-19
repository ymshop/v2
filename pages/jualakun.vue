<template>
  <div class="flex flex-col justify-center my-5 select-text">
    <h3
      class="flex flex-col space-y-3 text-lg font-normal leading-relaxed tracking-wide text-center"
    >
      <span>
        Kamu pengen jual akun game? Bingung mau posting dimana? Tenang kita
        punya solusinya.
      </span>
      <span>
        Ayo pakai jasa jual akun dari YMSHOP, akun anda akan kami posting di
        <a
          href="https://instagram.com/ymshop28"
          target="_blank"
          class="font-medium underline transition-colors duration-200 hover:text-blue-600"
        >Instagram</a>
        kami.
      </span>
      <span>
        Caranya gampang kok kamu tinggal isi aja data yang ada dibawah dan klik
        tombol
        <span
          class="px-2 py-1 text-sm text-white bg-blue-600 rounded select-none"
        >kirim data</span>
      </span>
    </h3>

    <!-- form -->
    <div class="grid grid-cols-12 gap-2 mt-5">
      <!-- game -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Game
        <div class="relative">
          <select
            id="select"
            class="block w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded appearance-none focus:outline-none focus:border-blue-600 focus:text-blue-600"
            v-model="form.game"
            v-focus
          >
            <option v-for="(game, index) in games" :key="index">
              {{
              game
              }}
            </option>
          </select>
          <div
            id="arrow_select"
            class="absolute inset-y-0 top-0 right-0 flex items-center px-2 text-gray-300 transition-colors duration-200"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
              <path
                fill-rule="evenodd"
                d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                clip-rule="evenodd"
              />
            </svg>
          </div>
        </div>
      </label>

      <!-- nickname -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Nickname
        <input
          type="text"
          v-model="form.nickname"
          class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
          autocomplete="off"
        />
      </label>

      <!-- level -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Level
        <input
          type="text"
          v-model="form.level"
          class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
          autocomplete="off"
        />
      </label>

      <!-- harga -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Harga
        <input
          type="text"
          v-model="form.harga"
          class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
          autocomplete="off"
          v-currency="{ currency: 'IDR', locale: 'id' }"
        />
      </label>
      <span class="col-span-12 mx-2 -mt-2 text-sm text-red-600">*minimal Rp 250.000,00</span>

      <!-- keterangan -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Keterangan
        <textarea
          rows="10"
          v-model="form.keterangan"
          class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
          autocomplete="off"
        ></textarea>
      </label>

      <!-- caption -->
      <label class="col-span-12 mt-3 text-gray-700">
        Contoh Caption
        <div
          class="w-full px-4 py-2 text-gray-500 bg-transparent border-2 border-gray-300 rounded"
          v-html="caption"
        ></div>
      </label>

      <!-- pilih admin -->
      <div class="flex justify-between col-span-12 mt-4 space-x-2 select-none">
        <a
          target="_blank"
          v-for="(admin, nomor, index) in admins"
          :key="index"
          :href="'https://wa.me/?phone=' + nomor + '&text=' + pesan"
          class="w-full px-4 py-3 text-center text-white transition-colors duration-200 bg-blue-600 rounded hover:bg-blue-700 focus:bg-blue-700 focus:outline-none"
        >{{ admin }}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "jual-akun.page",
  data() {
    return {
      form: {
        game: "",
        nickname: "",
        level: "",
        harga: "",
        keterangan: "",
      },
      admins: {
        6285210031615: "Kirim Data",
      },
      games: [
        "Arena Of Valor",
        "Call Of Duty Mobile",
        "Free Fire",
        "Mobile Legends: Bang Bang",
        "PlayerUnknown's Battlegrounds Mobile",
      ],
    };
  },

  computed: {
    pesan() {
      let enter = "%0A";
      let lb = " ㅤㅤㅤㅤㅤㅤ ";
      let txt = "";
      let keterangan = this.form.keterangan;

      txt += `JUAL AKUN ${this.form.game.toUpperCase()}${enter}`;
      txt += `${lb}${enter}`;
      txt += `KETERANGAN AKUN${enter}`;
      txt += `Nickname: ${this.form.nickname}${enter}`;
      txt += `Level: ${this.form.level}${enter}`;
      txt += `Harga: ${this.form.harga}${enter}`;
      txt += `Keterangan: ${enter}${this.form.keterangan.replace(
        /\n|\r/g,
        enter
      )}${enter}`;
      txt += `${lb}${enter}`;
      txt += `TRANSAKSI WAJIB MENGGUNAKAN JASA REKBER/PULBER YMSHOP UNTUK MENGHINDARI TINDAKAN PENIPUAN${enter}`;
      txt += `${lb}${enter}`;
      txt += `APABILA ADA KEJADIAN TIPU MENIPU KARENA TIDAK MELAKUKAN REKBER/PULBER DENGAN ADMIN, MAKA ITU DILUAR TANGGUNG JAWAB KAMI.${enter}`;
      txt += `${lb}${enter}`;
      txt += `Kontak Admin${enter}`;
      txt += `WA: 085210031615${enter}`;
      txt += `${lb}${enter}`;
      txt += `Mau jual akun juga? Silahkan hubungi admin dengan kontak diatas.`;

      return txt;
    },
    caption() {
      let enter = "<br />";
      let txt = "";
      let keterangan = this.form.keterangan;

      txt += `JUAL AKUN ${this.form.game.toUpperCase()}${enter}`;
      txt += `${enter}`;
      txt += `KETERANGAN AKUN${enter}`;
      txt += `Nickname: ${this.form.nickname}${enter}`;
      txt += `Level: ${this.form.level}${enter}`;
      txt += `Harga: ${this.form.harga}${enter}`;
      txt += `Keterangan: ${enter}${this.form.keterangan.replace(
        /\n|\r/g,
        enter
      )}${enter}`;
      txt += `${enter}`;
      txt += `TRANSAKSI WAJIB MENGGUNAKAN JASA REKBER/PULBER YMSHOP UNTUK MENGHINDARI TINDAKAN PENIPUAN.${enter}`;
      txt += `${enter}`;
      txt += `APABILA ADA KEJADIAN TIPU MENIPU KARENA TIDAK MELAKUKAN REKBER/PULBER DENGAN ADMIN, MAKA ITU DILUAR TANGGUNG JAWAB KAMI.${enter}`;
      txt += `${enter}`;
      txt += `Kontak Admin${enter}`;
      txt += `WA: 085210031615${enter}`;
      txt += `${enter}`;
      txt += `Mau jual akun juga? Silahkan hubungi admin dengan kontak diatas.`;

      return txt;
    },
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
textarea {
  resize: none;
}
</style>
