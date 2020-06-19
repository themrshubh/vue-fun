<template>
  <b-container style="padding: 0px; min-height:60vh">
    <b-row>
      <b-col>
        <h3 class="text-muted">Kanban-Board</h3>
        <p class="text-muted">
          A Kanban board is one of the tools that can be used to implement Kanban to manage work at a personal or organizational level.
          This component uses local data binding methods.
          This is a simple representation of the Kanban-Board. Feel free to add new items to your lists and have fun dragging the tiles around.
        </p>
      </b-col>
    </b-row>
    <b-row>
      <b-col class="form-inline">
        <b-form-input class="dark-input border-0 shadow-none text-light" v-model="newTask" placeholder="New" @keyup.enter="add"></b-form-input><b-button class="ml-2 dark-button border-0 shadow-none" @click="add">Add</b-button>
      </b-col>
    </b-row>
    <div class="row mt-3">
      <div class="col-md-3 p-2 pl-3">
        <div class="p-2 alert alert-custom-1">
          <h3 class="todo">To-do</h3>
          <draggable class="list-group board-height" :list="todo" group="tasks">
            <div style="margin:5px" class="list-group-item kanban-card rounded text-light" v-for="element in todo" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3 p-2">
        <div class="p-2 alert alert-custom-2">
          <h3 class="planning">Planning</h3>
          <draggable class="list-group board-height" :list="plan" group="tasks">
            <div style="margin:5px" class="list-group-item kanban-card rounded text-light" v-for="element in plan" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3 p-2">
        <div class="p-2 alert alert-custom-3">
          <h3 class="inprogress">In Progress</h3>
          <draggable class="list-group board-height" :list="inprogress" group="tasks">
            <div style="margin:5px" class="list-group-item kanban-card rounded text-light" v-for="element in inprogress" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3 p-2 pr-3">
        <div class="p-2 alert alert-custom-4">
          <h3 class="done">Done</h3>
          <draggable class="list-group board-height" :list="done" group="tasks">
            <div style="margin:5px" class="list-group-item kanban-card rounded text-light" v-for="element in done" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </b-container>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  components:{
    draggable
  },
  data() {
    return {
      newTask: '',
      todo: [
        {name: "Water the plants"},
        {name: "Sanitize everything"},
        {name: "Find a covid cure"},
        {name: "Make pizza"},
      ],
      plan:[],
      inprogress:[],
      done:[]
    }
  },
  methods:{
    add(){
      if(this.newTask){
        this.todo.push({name: this.newTask});
        this.newTask = ''
      }
    }
  }
}
</script>

<style scoped>
  .board-height{
    min-height: 40vh;
  }

  .list-group-item:hover{
    cursor: grab
  }

  .dark-input{
    background-color: rgba(63, 63, 63, 0.315);
  }

  .dark-input:focus{
    background-color: rgba(58, 58, 58, 0.452);
  }

  .dark-button{
    background-color:rgba(104, 104, 104, 0.137) !important;
    color:rgb(199, 199, 199)
  }

  .dark-button:hover{
    background-color: rgba(0, 0, 0, 0.247);
    background-image: linear-gradient(to bottom right, rgba(255, 0, 179, 0.281), rgba(0, 140, 255, 0.404));
    color:rgb(212, 212, 212)
  }

  .todo{
    color: rgba(255, 0, 179, 1)
  }

  .planning{
    color: rgba(162, 0, 255, 1);
  }

  .inprogress{
    color: rgba(76, 0, 255, 1);
  }

  .done{
    color:rgba(0, 140, 255, 1);
  }

  .alert-custom-1{
    background-color:rgba(255, 0, 179, 0.15);
  }

  .alert-custom-2{
    background-color:rgba(162, 0, 255, 0.15);
  }

  .alert-custom-3{
    background-color:rgba(76, 0, 255, 0.150);
  }

  .alert-custom-4{
    background-color:rgba(0, 140, 255, 0.15);
  }

  .kanban-card{
    background-color: rgba(167, 167, 167, 0.096);
  }
</style>