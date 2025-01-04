<template>
  <div class="col-12">
    <div class="card col-10 col-lg-3 col-md-6 col-sm-6">
      <div class="card-header">
        <h3><strong>TO-DO LIST</strong></h3>
      </div>
      <InputGroup1 @data-item ="handleValue"/>
      <div class="card-body">
        <ul>
        <TodoItems :items="tasks" @delete-task="deleteTask"/>
        
      </ul>

      </div>
     
      <div class="card-footer">
        <div class="footer-content">
          <div class="itens-count">
            <a href="#"> Tasks: {{ tasks.filter(i => i.checked == false).length  }}</a>

          </div>
          <div class="delete-itens">
            <a href="#" @click="deleteAll"><i class="bi bi-trash3-fill"></i></a>

          </div>
          
        </div>
        
      </div>
      
  </div>

  </div>

</template>

<script>
import InputGroup1 from './components/input-group-1/InputGroup1.vue';
import TodoItems from './components/todoItems/TodoItems.vue';

// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    InputGroup1,
    TodoItems,
  },
  data(){
    return{
      tasks: []
    }
  }, 
  methods:{
    handleValue(value){
      if(value.trim() != "")
      this.tasks.push({text:value, checked:false})
    },
    deleteTask(index){
      this.tasks.splice(index, 1)

    },
    deleteAll(){
      this.tasks = []

    }
   
  }
}
</script>

<style>
body{
 background: linear-gradient(45deg, #002135, #4682B4);
    background-color: rgba(0, 0, 0, 0);
  height: 100vh;
;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul{
  padding: 15px;
}
.card{
  margin: 0 auto;
  padding: 25px;
}
.card .card-body{
  height: 200px;
  overflow: auto;
}
.card .card-footer .footer-content{
  display: flex;
  justify-content: space-between;
  
}
.card .card-footer .footer-content a{
  text-decoration: none;
  color: #6c757d;
}

</style>
