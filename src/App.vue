<template>
  <div class="container mt-5">
    <div class="row">
      <div class = "col form-inline">
        <b-form-input v-model="newTask" placeholder="Enter a Task here..." @keyup.enter=addTask></b-form-input> <b-button class="ml-2" variant="primary" @click="addTask">Add</b-button>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>To-Do</h3>
          <draggable class="list-group kanban-column" :list ="arrToDo" group="tasks">
            <div class="list-group-item" v-for="element in arrToDo" :key="element.title">
              {{element.title}}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group kanban-column" :list ="arrInProgress" group="tasks">
            <div class="list-group-item" v-for="element in arrInProgress" :key="element.title">
              {{element.title}}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>In Testing</h3>
          <draggable class="list-group kanban-column" :list ="arrInTesting" group="tasks">
            <div class="list-group-item" v-for="element in arrInTesting" :key="element.title">
              {{element.title}}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Completed</h3>
          <draggable class="list-group kanban-column" :list ="arrCompleted" group="tasks">
            <div class="list-group-item" v-for="element in arrCompleted" :key="element.title">
              {{element.title}}
            </div>
          </draggable>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";



export default {
  name: 'App',
  components: {
    draggable
  },
  data(){
    return {
      newTask: "",
      arrToDo:[
        {title: "Start Coding"},
        {title: "Design the UI"},
        {title: "Learn Vue.js and React.js"},
        {title: "Review Coding"},
      ],
      arrInProgress:[],
      arrInTesting:[],
      arrCompleted:[],
    }
  },
  methods:{
    addTask() {
      if(this.newTask){
        this.arrToDo.push({title: this.newTask});
        this.newTask="";
      }
    }
  }
}
</script>


<style>
.kanban-column{
  min-height: 300px;
}
</style>
