<template>
  <div class="w-screen h-screen bg-gray-300 select-none">
    <div class="flex justify-center w-full h-full">
      <div class="w-full max-w-md max-h-full min-h-full overflow-y-auto bg-white shadow-xl">
        <Navbar></Navbar>
        <div class="container w-full h-full pt-16 -mt-16">
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

<style>
::-webkit-scrollbar {
  width: 0;
}
</style>
