<template>
  <div id="app">
    <div class="container">
      <h1>My TODO</h1>
      <input
        class="input"
        v-model="newToDo" 
      />
      <button class="add-button" v-on:click="add()">Add</button> 
      <ul style="list-style-type: none;">
        <li v-for="(todo,i) in existingToDo">
          <span>
            {{i + 1}}: {{todo.text}}
          </span>
          <button class="delete-button" @click="deleteToDo(i)">
            X
          </button>
        </li>  
      </ul> 
    </div>    
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      newToDo: '',
      existingToDo: [
        {text: 'Sleep', id:0},
        {text: 'Feed Cat', id:1},
        {text: 'Buy Milk', id:2}
      ]
    }
  },
  methods:{
    add(){
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
      this.newToDo=''
    },
    deleteToDo(i){
      this.existingToDo.splice(i,1)
    }
  }
}
</script>

<style>
  .center {
    margin: auto;
    width: 50%;
    border: 3px solid green;
    padding: 10px;
  }
  h1 {
    color: black;
    font-family: verdana;
    font-size: 300%;
  }
</style>
