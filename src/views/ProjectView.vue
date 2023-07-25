<script setup>
import ProjectHeader from '../components/ProjectHeader.vue';
import KanbanBoard from '../components/KanbanBoard.vue';

import { RouterLink } from 'vue-router'
import 'bootstrap/dist/css/bootstrap.min.css';

</script>

<template>

  <nav class="nav">
    <RouterLink to="/" class="nav-link nav-brand" aria-current="page">Brello</RouterLink>
  </nav>

  <main>
    <ProjectHeader />
    <KanbanBoard />
  </main>

</template>

<style>
* {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

body {
  background-color: #FFF4EB;
}

.nav {
  margin: 2%;
}

.nav-brand {
  color: #DE6700;
  font-weight: bold;
  font-size: 6rem;
}

</style>
