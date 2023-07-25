<script>
import axios from 'axios'

export default {
  data() {
    return {
      projects: []
    }
  },
  mounted() {
    axios
      .get('http://localhost:5002/projects')
      .then((response) => {
          this.projects = response.data
    })
  },
  methods: {
    get_project(id) {
      axios
      .get(`http://localhost:5002/project/${id}`)
      .then((response) => console.log(response))
    }
  }
}
</script>

<template>

<!-- List existing projects -->
  <section class="list-group">
    <template v-for="project in projects" :key="project.id">
        <router-link :to="{ name: 'projects', params: {id: project.id}}">
          <button type="button" class="list-group-item list-group-item-action"> {{ project.name }}</button>
        </router-link>
    </template>
  </section>

</template>

<style>

</style>