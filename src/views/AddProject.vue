<template>
  <form
    @submit.prevent="handleSubmit"
    class="bg-white p-5 rounded-lg shadow-lg"
  >
    <label class="block text-gray-500 text-xl lg:text-2xl font-bold mt-5 mb-2"
      >Title:</label
    >
    <input
      type="text"
      v-model="title"
      class="
        p-2
        lg:p-3
        text-xl
        lg:text-2xl
        focus:
        outline-none
        border-b-2 border-gray-500
        w-full
        border-box
      "
    />
    <label class="block text-gray-500 text-xl lg:text-2xl font-bold mt-5 mb-2"
      >Details:</label
    >
    <textarea
      v-model="detail"
      class="
        text-xl
        lg:text-2xl
        rounded-lg
        border-2 border-gray-400
        focus:
        outline-none
        p-2
        w-full
        h-60
      "
    ></textarea>

    <button
      class="
        bg-green-600
        text-gray-200
        hover:bg-green-400 hover:text-gray-100 hover:shadow-2xl
        p-3
        border-0
        rounded-lg
        text-xl
        lg:text-2xl
        items-end
        shadow-lg
      "
    >
      Add Project
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      detail: "",
    };
  },
  methods: {
    handleSubmit() {
      let project = {
        title: this.title,
        details: this.detail,
        complete: false,
      };

      fetch("http://localhost:3000/projects", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(project),
      }).then(() => {
        this.title = "";
        this.detail = "";
        this.$router.push("/");
      });
    },
  },
};
</script>

<style lang="scss" scoped></style>
