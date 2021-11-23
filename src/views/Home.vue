<template>
  <div v-if="projects.length">
    <div v-for="project in projects" :key="project.id">
      <Project :project="project" @delete="handleDelete" />
    </div>
  </div>
</template>

<script>
import Project from "../components/Project.vue";
export default {
  name: "home",
  components: {
    Project,
  },
  data() {
    return {
      projects: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/projects")
      .then((response) => response.json())
      .then((data) => (this.projects = data));
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => project.id != id);
    },
  },
};
</script>

<style lang="scss" scoped></style>
