<template>
  <div class="home">
    <h1>Home</h1>
    <div v-for="project in projects" :key="project.id">
      <SingleProject :project="project" @delete="deleteProject"></SingleProject>
    </div>
  </div>
</template>

<script>
import SingleProject from '@/components/SingleProject.vue';
export default {
  name: 'Home',
  components: {
    SingleProject
  },
  data() {
    return {
      projects: []
    }
  },
  methods: {
    deleteProject(id) {
      this.projects = this.projects.filter(project => {
        return project.id != id;
      })
    }
  },
  mounted() {
    fetch("http://127.0.0.1:3000/projects")
      .then((response) => {
        return response.json();
      })
      .then((datas) => {
        this.projects = datas
      })
      .catch((err) => {

      })
  }
}
</script>

<style>
.home {
  width: 500px;
}
</style>