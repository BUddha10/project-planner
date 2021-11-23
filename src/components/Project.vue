<template>
  <div
    class="
      mb-10
      bg-gray-100
      px-4
      py-6
      rounded-lg
      border-1 border-l-8 border-red-400
      shadow-lg
    "
  >
    <div class="flex justify-between items-center">
      <h3 class="cursor-pointer" @click="showDetail = !showDetail">
        {{ project.title }}
      </h3>
      <div class="flex space-x-4 cursor-pointer">
        <span class="material-icons text-gray-400 hover:text-gray-700">
          edit
        </span>
        <span class="material-icons text-gray-400 hover:text-gray-700">
          delete
        </span>
        <span class="material-icons text-gray-400 hover:text-gray-700">
          done
        </span>
      </div>
    </div>

    <div v-if="showDetail">
      <p class="text-2xl mt-4 text-gray-700">{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetail: false,
    };
  },
};
</script>

<style lang="scss" scoped></style>
