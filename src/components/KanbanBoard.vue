<script>
import draggable from "vuedraggable";
import axios from 'axios';
//   import Task from './Task.vue';

export default {
  mounted() {
    axios
      .get(`http://localhost:5002/projects/${this.$route.params.id}/tasks`)
      .then((response) => {
        const tasks = response.data
        this.tasks = {
          toDo: tasks.filter(task => task.status === 'toDo'),
          upNext: tasks.filter(task => task.status === 'upNext'),
          doing: tasks.filter(task => task.status === 'doing'),
          done: tasks.filter(task => task.status === 'done')  
        }
      })
  },
  components: {
    draggable,
  },
  methods: {
    log: function(evt) {
      window.console.log(evt);
    },
    update_task(event) {
      console.log(event)
      // axios
      // .put(`http://localhost:5002/projects/${this.$route.params.id}/${itemKey}`, )
      // .then((response) => console.log(response))
    }
  },
  data() {
    return {
      tasks: {
        toDo: [],
        upNext: [],
        doing: [],
        done: []
      }
    };
  },
};
</script>

<template>
    <main>
      <div class="m-5 container">
        <div class="row">

          <section class="col todoCol">
            <h2>To Do</h2>
            <draggable class="task" @end="update_task" group="tasks" :list="tasks.toDo" tag="div" itemKey="task.id">
              <template #item="{ element: task }">
                <div class="todo">
                  <p class="name">{{ task.name }} <span class="badge text-bg-light">{{ task.priority }}</span></p>                  <div class="summary">
                    <p>{{ task.summary }}</p>
                  </div>
                </div>
              </template>
            </draggable>
          </section>

          <section class="col upnextCol">
            <h2>Up Next</h2>
            <draggable class="task" @end="update_task" group="tasks" v-model="tasks.upNext" tag="div" itemKey="task.id">
              <template #item="{ element: task }">
                <div class="upnext">
                  <p class="name">{{ task.name }} <span class="badge text-bg-light">{{ task.priority }}</span></p>                  <div class="summary">
                    <p>{{ task.summary }}</p>
                  </div>
                </div>
              </template>
            </draggable>
          </section>

          <section class="col doingCol">
            <h2>Doing</h2>
            <draggable class="task" @end="update_task" group="tasks" v-model="tasks.doing" tag="div" itemKey="task.id">
              <template #item="{ element: task }">
                <div class="doing">
                  <p class="name">{{ task.name }} <span class="badge text-bg-light">{{ task.priority }}</span></p>                  <div class="summary">
                    <p>{{ task.summary }}</p>
                  </div>
                </div>
              </template>
            </draggable>
          </section>

          <section class="col doneCol">
            <h2>Done</h2>
            <draggable class="task" @end="update_task" group="tasks" v-model="tasks.done" tag="div" itemKey="task.id">
              <template #item="{ element: task }">
                <div class="done">
                  <p class="name">{{ task.name }} <span class="badge text-bg-light">{{ task.priority }}</span></p>
                  <div class="summary">
                    <p>{{ task.summary }}</p>
                  </div>
                </div>
              </template>
            </draggable>
          </section>

        </div>
      </div>
    </main>

</template>


<style scoped>
  .col {
    margin: 5px;
    border-radius: 50% 20% / 10% 40%;
  }

  .todo, .upnext, .doing, .done {
    border: 1px solid;
  }

  h2 {
    font-weight: bold;
    font-size: 3rem;
  }
  .name {
    font-size: 1.5rem;
  }

  .summary {
    font-size: 1rem;
  }

  .todoCol {
    background-color: #F48C3D;
  }
  .upnextCol {
    background-color: #F9AE40;
  }
  .doingCol {
    background-color: #FADC18;
  }
  .doneCol {
    background-color: #26C9C9;
  }

</style>