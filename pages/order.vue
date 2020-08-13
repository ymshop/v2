<template>
  <div class="flex flex-col justify-center my-5 select-text">
    <h3 class="text-lg font-normal leading-relaxed tracking-wide text-center">
      Untuk Pembelian Bisa Dengan Cara Kalian Isi Data Dibawah Ini Dan Pilih
      Ingin Bertransaksi Melalui Admin Yang Mana.
      <span
        class="block mt-4 text-base font-light"
      >*semua admin baik kok 😊</span>
    </h3>

    <!-- form -->
    <div class="grid grid-cols-12 gap-2 mt-5">
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
          v-focus
        />
      </label>

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

      <!-- keterangan topup: login -->
      <template
        v-if="
          form.game == 'Arena Of Valor' || form.game == 'Call Of Duty Mobile'
        "
      >
        <span class="col-span-12 px-2 text-sm italic font-normal tracking-wide text-gray-700">
          top up game
          <span class="font-medium text-gray-900">{{ form.game }}</span>
          dilakukan via login, jadi berikan akun anda kepada admin yang
          bersangkutan
        </span>
      </template>

      <!-- topup: id -->
      <template
        v-if="
          form.game == 'Free Fire' ||
            form.game == 'Mobile Legends: Bang Bang' ||
            form.game == 'PlayerUnknown\'s Battlegrounds Mobile'
        "
      >
        <label
          class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
        >
          Akun ID
          <input
            type="text"
            v-model="form.akun"
            class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
            autocomplete="off"
          />
        </label>
      </template>

      <!-- jumlah top up -->
      <template v-if="form.game != ''">
        <label
          class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
        >
          Jumlah
          <span v-if="form.game == 'Arena Of Valor'">Voucher</span>
          <span v-if="form.game == 'Call Of Duty Mobile'">COD Point</span>
          <span v-if="form.game == 'Free Fire'">Diamond</span>
          <span v-if="form.game == 'Mobile Legends: Bang Bang'">Diamond</span>
          <span v-if="form.game == 'PlayerUnknown\'s Battlegrounds Mobile'">Unknown Cash</span>
          <input
            type="text"
            v-model="form.jumlah"
            class="w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded focus:text-blue-600 focus:outline-none focus:border-blue-600"
            autocomplete="off"
          />
        </label>
      </template>

      <!-- metode pembayaran -->
      <label
        class="col-span-12 text-gray-700 transition-colors duration-200 focus-within:text-blue-600"
      >
        Metode Pembayaran
        <div class="relative">
          <select
            id="select"
            class="block w-full px-4 py-2 text-gray-500 transition-colors duration-200 bg-transparent border-2 border-gray-300 rounded appearance-none focus:outline-none focus:border-blue-600 focus:text-blue-600"
            v-model="form.pembayaran"
          >
            <option v-for="(pembayaran, index) in metode" :key="index">
              {{
              pembayaran
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
  name: "order.page",
  data() {
    return {
      form: {
        nickname: "",
        game: "",
        jumlah: "",
        akun: "",
        pembayaran: "",
      },
      games: [
        "Arena Of Valor",
        "Call Of Duty Mobile",
        "Free Fire",
        "Mobile Legends: Bang Bang",
        "PlayerUnknown's Battlegrounds Mobile",
      ],
      metode: [
        "Alfamart",
        "Indomaret",
        "BCA",
        "Dana",
        "Gopay",
        "Pulsa (XL / AXIS / TELKOMSEL)",
      ],
      admins: {
        6285210031615: "Admin 1",
        6281283379939: "Admin 2",
      },
    };
  },

  computed: {
    pesan() {
      let enter = "%0A";
      let pesan = "";
      let satuan = "";

      // satuan beli
      if (this.form.game == "Arena Of Valor") satuan = "Voucher";
      if (this.form.game == "Call Of Duty Mobile") satuan = "COD Point";
      if (this.form.game == "Free Fire") satuan = "Diamond";
      if (this.form.game == "Mobile Legends: Bang Bang") satuan = "Diamond";
      if (this.form.game == "PlayerUnknown's Battlegrounds Mobile")
        satuan = "Unknown Cash";

      // via login
      if (
        this.form.game == "Arena Of Valor" ||
        this.form.game == "Call Of Duty Mobile"
      ) {
        pesan += `Assalamu'alaikum, mau *Top Up* nih${enter}`;
        pesan += `${enter}`;
        pesan += `*Nickname*: ${this.form.nickname}${enter}`;
        pesan += `*Game*: ${this.form.game}${enter}`;
        pesan += `*Jumlah COD Point*: ${this.form.jumlah}${enter}`;
        pesan += `*Metode Pembayaran*: ${this.form.pembayaran}${enter}`;
        pesan += `${enter}`;
        pesan += `_top up game *${this.form.game}* dilakukan via login, jadi berikan akun anda kepada admin yang bersangkutan_`;

        return pesan;
      }

      // via non-login
      pesan += `Assalamu'alaikum, mau *Top Up* nih${enter}`;
      pesan += `${enter}`;
      pesan += `*Nickname*: ${this.form.nickname}${enter}`;
      pesan += `*Game*: ${this.form.game}${enter}`;
      pesan += `*Akun*: ${this.form.akun}${enter}`;
      pesan += `*Jumlah ${satuan}*: ${this.form.jumlah}${enter}`;
      pesan += `*Metode Pembayaran*: ${this.form.pembayaran}${enter}`;

      return pesan;
    },
  },

  head() {
    return {
      title: "YMSHOP — Order | Tempat Top Up Game Aman dan Cepat",
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
