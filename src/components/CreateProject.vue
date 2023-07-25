<script>
import axios from 'axios'

export default {
  data() {
    return {
        project: {
            name: '',
        }
    }
  },
  methods: {
    add_project() {
        axios
        .post('http://localhost:5002/projects', this.project)
        .then((response) => {
            const project = response.data
            this.$router.push({ name: 'projects', params: { id: project.id } })
        })
    }
  }
}

</script>

<template>
    
<!-- create new project form -->
<section>
    <form @submit.prevent="add_project">
      <div>
        <label for="name">Project name: </label>
        <input type="text" id="name" v-model="project.name" class="m-2" />
      </div>
      <button>+</button>
    </form>

</section>

</template>