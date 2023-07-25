<script>
import axios from 'axios'

export default {
  data() {
    return {
      project: {
        name: "",
        description: '',
        due_date: new Date()
      }
    }
  },
  mounted() {
    axios
        .get(`http://localhost:5002/projects/${this.$route.params.id}`)
        .then((response) => {
            this.project = response.data
        })
  },
  methods: {
    update_project() {
        axios
        .put(`http://localhost:5002/projects/${this.$route.params.id}`, this.project)
        .then((response) => console.log(response))
    }
  }
}
</script>

<template>

<section class="container projectInfo">

  <h1 class="my-4">{{ project.name }}</h1>

    <form>
      <div>
        <h4>{{ project.description }}</h4>
        <textarea @input="update_project" id="description" rows="6" cols="22" v-model="project.description" class="my-2" />
      </div>
      <div>
        <h5>Due by {{ project.due_date }}</h5>
        <input @input="update_project" type='date' id="due_date" v-model="project.due_date" class="my-2" />
      </div>
    </form>

</section>

</template>

<style scoped>

.projectInfo {
  margin: 2rem;
}

h1 {
  font-weight: bold;
  font-size: 4rem;
}

</style>