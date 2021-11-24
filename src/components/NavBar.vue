<template>
  <div
    class="
      flex
      items-center
      justify-center
      mb-8
      text-2xl text-gray-500
      space-x-8
    "
  >
    <router-link :to="{ name: 'Home' }" class="hover:text-gray-800"
      >Projects</router-link
    >
    <router-link :to="{ name: 'AddProject' }" class="hover:text-gray-800"
      >Add New Project</router-link
    >
  </div>
</template>

<script>
export default {};
</script>
