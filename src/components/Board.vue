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
      <b-col class="pr-md-0" cols="md-3">
        <b-form-input class="dark-input border-0 shadow-none text-light" v-model="newTask" placeholder="New" @keyup.enter="add"></b-form-input>
      </b-col>
      <b-col>
        <b-button class="dark-button border-0 shadow-none" @click="add">Add</b-button>
      </b-col>
    </b-row>
    <div class="row mt-3">
      <div class="col-md-3 p-2 pl-md-3">
        <div class="p-2 alert alert-custom-1">
          <h3 class="todo">To-do</h3>
          <div class="board-height">
            <draggable class="list-group content" :list="todo" group="tasks">
                <div style="margin:5px;" class="list-group-item alert-custom-1 rounded text-light" v-for="element in todo" :key="element.index">
                  {{element.name}}
                </div>
            </draggable>
          </div>
        </div>
      </div>
      <div class="col-md-3 p-2">
        <div class="p-2 alert alert-custom-2">
          <h3 class="planning">Planning</h3>
          <div class="board-height">
            <draggable class="list-group content" :list="plan" group="tasks">
              <div style="margin:5px" class="list-group-item alert-custom-2 rounded text-light" v-for="element in plan" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
          </div>
          
        </div>
      </div>
      <div class="col-md-3 p-2">
        <div class="p-2 alert alert-custom-3">
          <h3 class="inprogress">In Progress</h3>
          <div class="board-height">
            <draggable class="list-group content" :list="inprogress" group="tasks">
              <div style="margin:5px" class="list-group-item alert-custom-3 rounded text-light" v-for="element in inprogress" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
          </div>
        </div>
      </div>
      <div class="col-md-3 p-2 pr-md-3">
        <div class="p-2 alert alert-custom-4">
          <h3 class="done">Done</h3>
          <div class="board-hight">
            <draggable class="list-group content" :list="done" group="tasks">
              <div style="margin:5px" class="list-group-item alert-custom-4 rounded text-light" v-for="element in done" :key="element.name">
                {{element.name}}
              </div>
            </draggable>
          </div>
        </div>
      </div>
    </div>
  </b-container>
</template>

<script>
import draggable from 'vuedraggable';

export default {
  components:{
    draggable,
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
      plan:[
        {name: "Check B.E Project"},
        {name: "Update LinkedIn"}
      ],
      inprogress:[
        {name: "Stanford: Algorithms"}
      ],
      done:[
        {name: "Black Book"},
        {name: "Develop Alexa Skill"},
        {name: "Configure AWS Gateway"},
        {name: "Deploy Flask API"},
      ]
    }
  },
  methods:{
    add(){
      if(this.newTask){
        this.todo.unshift({name: this.newTask});
        this.newTask = ''
      }
    },
    del(){

    }
  }
}
</script>

<style scoped>
  .board-height{
    height: 40vh;
  }

  .content{
    height: 40vh;
    overflow: auto
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
    background-color: rgba(255, 255, 255, 0.116) !important;
    color:rgb(212, 212, 212)
  }

  .todo{
    color: rgb(255, 0, 93)
  }

  .planning{
    color: rgba(255, 208, 0, 1);
  }

  .done{
    color: rgba(0, 195, 255, 1);
  }

  .inprogress{
    color:rgba(0, 255, 156, 1);
  }

  .alert-custom-1{
    background-color:rgba(255, 0, 93, 0.12);
  }

  .alert-custom-2{
    background-color:rgba(255, 208, 0, 0.12);
  }

  .alert-custom-3{
    background-color:rgba(0, 255, 156, 0.12);
  }

    .alert-custom-4{
    background-color:rgba(0, 195, 255, 0.12);
  }
</style>