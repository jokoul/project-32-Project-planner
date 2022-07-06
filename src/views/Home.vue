<template>
  <div class="home">
    <!--$event refers to the "by" data passed through $emit custom event-->
    <FilterNav @filterChange="current = $event" :current="current" />
    <!--Conditional showing with v-if-->
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id">
        <SingleProject
          :project="project"
          @delete="handleDelete"
          @complete="handleComplete"
        />
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from "../components/SingleProject.vue";
import FilterNav from "../components/FilterNav.vue";

export default {
  name: "Home",
  components: {
    SingleProject,
    FilterNav,
  },
  data() {
    return {
      projects: [],
      current: "all",
    };
  },
  mounted() {
    fetch("https://project-planner-joan.herokuapp.com/projects") //proxy : http://localhost:3000
      .then((res) => res.json())
      .then((data) => (this.projects = data))
      .catch((err) => console.log(err.message));
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id; //id is the second arguments of $emit method who specified custom event in child compoenent
      });
    },
    handleComplete(id) {
      let p = this.projects.find((project) => {
        return project.id === id;
      });
      //we find the first project wich comply the find condition
      p.complete = !p.complete;
    },
  },
  computed: {
    filteredProjects() {
      if (this.current === "completed") {
        return this.projects.filter((project) => project.complete === true);
      }
      if (this.current === "ongoing") {
        return this.projects.filter((project) => project.complete === false);
      }
      return this.projects;
    },
  },
};
</script>
