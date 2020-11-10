<template>
   <div>
     <h1>{{header}}:</h1>
      <input  type="text" class="task-input" v-model="task" v-on:keyup.enter="addTask(task)" title="пиши сюда">
      <button class="add-task" v-on:click="addTask(task)" title="Добавить цель">Добавить</button>
      <h2>Чтобы добавить цель напишите в поле и нажмите Enter или кнопку добавить</h2>
      <div class="item-task">
          <ul>
            <li 
            v-for="(task, index) in tasks.sort()" 
            :key="task">
            <input type="checkbox" 
            v-on:click="removeTask(index)">
            {{ task.toLowerCase() }}
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
      tasks: [ 'бросить курить', 'занятся спортом', ]
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
  },
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #033022be;
  margin-top: 60px;
}

h1{
  padding-bottom: 30px;
  text-align: center;
  font-family: 'ROBOTO', sans-serif, ;
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

.item-task > ul > li {
  padding-top: 20px;
}

.item-task > ul > li:hover{
  text-decoration: line-through;
  text-decoration-color: rgba(17, 153, 142, 0.986);
}
input[type="text"]{
  width: 400px;
  height: 50px;
  font-size: 22px;
  border-radius: 20px;
  margin: 0 auto;
  box-shadow: darkred 1px 1px 1px ;
  outline:none;
  text-align: center;
}
input[type="text"]:focus{
  border:darkcyan;
  outline: none;
}
button{
  width: 200px;
  height: 50px;
  margin: 30px;
  font-size: 22px;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  outline: none;
  border-radius: 20px;
  box-shadow: darkred 1px 1px 1px ;
}
button:hover {
  background:rgba(5, 38, 82, 0.493);
  transition: background, 1s ease-in-out;
}

</style>
