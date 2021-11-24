<template>
  <div class="min-h-screen min-w-full bg-gray-200">
    <div class="mx-auto pt-4 pb-10 w-4/6 items-center">
      <NavBar />
      <router-view />
    </div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
export default {
  components: {
    NavBar,
  },
};
</script>

<style lang="scss"></style>
