<template>
   <div>
     <h1>{{header}}:</h1>
      <input  type="text" class="task-input" v-model="task" v-on:keyup.enter="addTask(task)">
      <button class="add-task" v-on:click="addTask(task)">Добавить</button>
      <div class="item-task">
          <ul>
            <li 
            v-for="(task, index) in tasks" 
            :key="task">
            <input type="checkbox" 
            v-on:click="removeTask(index)">
            {{task}}
            </li>
          </ul>
      </div>
   </div>
</template>

<script>


export default {

  name: 'App',
  components: {
   
  },
  
  data(){
    return {
      task: '',
      header: 'Список дел',
      tasks: ['Бросить пить энергетики', 'бросить курить', 'занятся спортом']
    }
  },

  methods: {
    addTask(task){
      if(task){
        this.tasks.push(task);
        this.task = '';
      }
      
      
      
    },
    removeTask(index){
      this.tasks.splice(index, 1);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1{
  padding-bottom: 30px;
  color: white;
  text-align: center;
}

.item-task {
  margin-top: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 22px;
  color: white;
}

.item-task > ul {
  list-style-type: none;
}
.item-task > ul > li:hover{
  text-decoration: line-through;
  color: red;
}
input[type="text"]{
  width: 400px;
  height: 50px;
  font-size: 22px;
}
input[type="text"]:focus{
  border:darkcyan;
  outline: none;
}
button{
  width: 200px;
  height: 50px;
  font-size: 22px;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  outline: none;
}

</style>
