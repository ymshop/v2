<template>
  <div class="w-screen h-screen bg-gray-300 select-none">
    <div class="flex justify-center w-full h-full">
      <div class="w-full max-w-sm max-h-full min-h-full overflow-y-auto bg-white shadow-xl">
        <Navbar></Navbar>
        <div class="container w-full">
          <Nuxt />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";

export default {
  name: "default.layout",
  components: {
    Navbar,
  },
};
</script>
