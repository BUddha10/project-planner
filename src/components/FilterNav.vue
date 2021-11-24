<template>
  <div class="mb-5 text-xl font-bold text-gray-500 ml-4 flex space-x-8">
    <button
      type="button"
      :class="{
        ' text-gray-900 border-b-4 border-gray-600 shadow-lg':
          current === 'all',
      }"
      @click="filterProduct('all')"
    >
      ALL
    </button>
    <button
      type="button"
      :class="{
        ' text-gray-900 border-b-4 border-green-400 shadow-lg':
          current === 'complete',
      }"
      @click="filterProduct('complete')"
    >
      COMPLETE
    </button>
    <button
      type="button"
      :class="{
        ' text-gray-900 border-b-4 border-red-400 shadow-lg':
          current === 'ongoing',
      }"
      @click="filterProduct('ongoing')"
    >
      ONGOING
    </button>
  </div>
</template>

<script>
export default {
  props: ["current"],
  methods: {
    filterProduct(by) {
      this.$emit("changeFilter", by);
    },
  },
};
</script>
