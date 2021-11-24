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
    :class="{ 'border-green-400': project.complete }"
  >
    <div
      class="flex justify-between items-center text-2xl font-bold text-gray-700"
    >
      <h3 class="cursor-pointer" @click="showDetail = !showDetail">
        {{ project.title }}
      </h3>
      <div class="flex space-x-4 cursor-pointer">
        <router-link :to="{ name: 'EditProject', params: { id: project.id } }"
          ><span class="material-icons text-gray-400 hover:text-gray-700">
            edit
          </span></router-link
        >
        <span
          @click="deleteProject"
          class="material-icons text-gray-400 hover:text-gray-700"
        >
          delete
        </span>
        <span
          @click="toggleComplete"
          class="material-icons text-gray-400 hover:text-gray-700"
          :class="{ 'text-green-500': project.complete }"
        >
          done
        </span>
      </div>
    </div>

    <div v-if="showDetail">
      <p class="text-2xl mt-4 text-gray-600">{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetail: false,
      url: "http://localhost:3000/projects/" + this.project.id,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.url, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err));
    },
    toggleComplete() {
      fetch(this.url, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ complete: !this.project.complete }),
      })
        .then(() => this.$emit("complete", this.project.id))
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style lang="scss" scoped></style>
