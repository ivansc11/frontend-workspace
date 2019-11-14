<template>
  <div class="d-flex">
    <div class="tab w-25">
      <img class="m-3" src="../assets/avatar.png" alt />
      <h3>{{user.name}}</h3>
      <h5>{{user.role}}</h5>
    </div>
    <div class="briefing d-flex flex-column w-75">
      <div class="progress m-3">
        <div
          class="progress-bar progress-bar-striped progress-bar-animated bg-danger"
          role="progressbar"
          :style="'width:' + user.hoursRegistered + '%'"
          :aria-valuenow="user.hoursRegistered"
          aria-valuemin="0"
          :aria-valuemax="user.hoursPayed"
        >{{user.hoursRegistered}} hs</div>
      </div>
      <h6 class="mt-5">Metricas</h6>
      <div class="user-metrics rounded mr-4 ml-4"></div>
      <h6 class="mt-5">Tareas</h6>
      <div class="tasks overflow-auto h-50 mr-3 ml-3">
        <div class>
          <ul class="list-group">
            <li
              v-for="task in user.tasks"
              :key="task.name"
              class="task-item list-group-item list-group-item-light d-flex justify-content-sm-between"
            >
              <div class="d-flex flex-column">
                <h3 class="text-left">{{task.name}}</h3>
                <h6 class="text-left">{{task.description}}</h6>
              </div>
              <div class="options">
                <b-button @click="modalShow = !modalShow">
                  <img src="../assets/enter.png" alt />
                </b-button>
                <b-modal v-model="modalShow" @ok="deleteTask(task.name)" title="BootstrapVue">
                  <p class="my-4">Desea registrar la tarea?</p>
                </b-modal>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "Username",
        role: "Role",

        hoursRegistered: 25,
        hoursPayed: 100,
        projects: [],
        tasks: [
          {
            
            name: "task 1",
            done: false,
            description: "A task description"
          },
          {
            name: "task 2",
            done: false,
            description: "A task description"
          },
          {
            name: "task 3",
            done: false,
            description: "A task description"
          },
          {
            name: "task 4",
            done: false,
            description: "A task description"
          },
          {
            name: "task 5",
            done: false,
            description: "A task description"
          },
          {
            name: "task 6",
            done: false,
            description: "A task description"
          }
        ]
      },
      modalShow: false
    };
  },
  methods: {
    deleteTask: function(index) {
      this.user.tasks.splice(index,1)
    }
  },
  computed: {
    getUndoneTasks: function() {
      return this.user.tasks.filter(i => !i.done);
    }
  }
};
</script>

<style>
.tab {
  background-color: rgb(255, 255, 255);
}
.briefing {
  height: 50em;
  background-color: rgb(255, 255, 255);
}
.user-metrics{
  height: 20em;
  background-color: rgb(231, 231, 231);
  
}
.task-item {
  font-size: 1.5em;
  height: 5em;
}
</style>