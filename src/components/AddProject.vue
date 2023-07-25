<script setup>
import SelectProject from './SelectProject.vue';
import CreateProject from './CreateProject.vue';

</script>

<template>
 <section class="container">
    <div class="card">
      <div class="card-body">
        <h4 class="card-title">Create a new project</h4>
        <div class="row">
          <div class="col">
            <CreateProject />
          </div>
        </div>
        <div class="row">
          <div class="col">
            <h4 class="card-title">or select one</h4>
            <SelectProject />
          </div>
        </div>
      </div>
    </div>
  </section> 
</template>
