<template>
  <FilterNav @changeFilter="current = $event" :current="current" />
  <div v-if="projects.length">
    <div v-for="project in filterProject" :key="project.id">
      <Project
        :project="project"
        @delete="handleDelete"
        @complete="handleComplete"
      />
    </div>
  </div>
</template>

<script>
import Project from "../components/Project.vue";
import FilterNav from "../components/FilterNav.vue";
export default {
  name: "home",
  components: {
    Project,
    FilterNav,
  },
  data() {
    return {
      projects: [],
      current: "all",
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
    handleComplete(id) {
      let p = this.projects.find((project) => {
        return project.id === id;
      });
      p.complete = !p.complete;
    },
  },
  computed: {
    filterProject() {
      if (this.current === "complete") {
        return this.projects.filter((project) => project.complete);
      }
      if (this.current === "ongoing") {
        return this.projects.filter((project) => !project.complete);
      }
      return this.projects;
    },
  },
};
</script>
