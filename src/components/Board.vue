<template>
  <div class="container" style="padding: 0px">
    <div class="row">
      <div class="col form-inline">
        <b-form-input v-model="newTask" placeholder="New" @keyup.enter="add"></b-form-input><b-button class="ml-2" variant="primary" @click="add">Add</b-button>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>To-do</h3>
          <draggable class="list-group board-height" :list="todo" group="tasks">
            <div style="margin:5px" class="list-group-item" v-for="element in todo" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>Planning</h3>
          <draggable class="list-group board-height" :list="plan" group="tasks">
            <div style="margin:5px" class="list-group-item" v-for="element in plan" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>In Progress</h3>
          <draggable class="list-group board-height" :list="inprogress" group="tasks">
            <div style="margin:5px" class="list-group-item" v-for="element in inprogress" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group board-height" :list="done" group="tasks">
            <div style="margin:5px" class="list-group-item" v-for="element in done" :key="element.name">
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
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
    min-height: 100px;
  }

  .list-group-item:hover{
    cursor: grab
  }
</style>