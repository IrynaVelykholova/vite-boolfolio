<script>
import axios from 'axios';
  export default {
    data() {
      return {
        projects: [],
      };
    },
    methods: {
      fetchData() {
        axios.get("http://127.0.0.1:8000/api/projects")
        .then((response) => {
          this.projects = response.data;
          console.log(response);
        })
      },
      getImgUrl(project) {
        return `http://127.0.0.1:8000/storage/${project.image}`
      }
    },
    mounted() {
      this.fetchData();
    }
  }
</script>

<template>
  <h1 class="mb-3">HELLO</h1>

  <div class="card" style="width: 18rem;"
      v-for="project in projects" :key="project.id">
  <img :src="getImgUrl(project)" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ project.title }}</h5>
    <p class="card-text"> {{  project.description }}</p>
  </div>
</div>
</template>

<style scoped>

</style>
