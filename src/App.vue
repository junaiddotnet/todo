<template>
  <div id="app">
   <h2 class="bg-primary text-white text-center p-2">{{name}} To Do List</h2>
  
   <div class="container-fluid p4">
      <div class="row" v-if="filteredTask.length ==0">
     <div class="col text-center">
       <b class="h3">
         Nothing to do
       </b>
     </div>
    </div>
<template v-else>
     <div class="row">
       <div class="col font-weight-bold">
         Task
       </div>
       <div class="col-2 font-weight-bold">
        
         Done
       </div>
     </div>
    
     <div class="row" v-for="t in filteredTask" v-bind:key="t.action">
         <div class="col">
         {{t.action}}
       </div>
       <div class="col-2">
          <input type="checkbox" v-model="t.done" class="form-check-input"/>
         {{t.done}}
       </div>

     </div>
  </template>
     <div class="row py-2">
       <div class="col">
         <input class="form-control" v-model="newText"/>
       </div>
       <div class="col-2">
         <button class="btn btn-primary" v-on:click="addNew">Add</button>
       </div>
     </div>
     <div class="row bg-secondary py-2 mt-2 text-white">
      <div class="col text-center">
      <input type="checkbox" v-model="hideCompleted" class="form-check-input" />
      <label class="form-check-label font-weight-bold">
      Hide completed tasks
      </label>
      </div>
  </div>
   </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data(){
    return {
      name:'Junaid',
      task:[
        {action:'buy flower',done:false},
        {action:'buy water',done:true},
        {action:'buy cloths',done:false},
        {action:'buy cricket',done:true},
        {action:'buy house',done:true},
        {action:'buy food',done:false}
      ],
      hideCompleted:true,
      newText:""
    }
    },
    computed:{
      filteredTask(){
        return this.hideCompleted ?
        this.task.filter(t => t.done==false) : this.task
      }

  },
  
      methods:{
        addNew(){
          this.task.forEach(element => {
            if (element.action==this.newText)
            {
              alert("Already Exist");
              return false;
            }
          });
          this.task.push({
            action:this.newText,
            done:false
          });
          localStorage.setItem("todos", JSON.stringify(this.tasks));
        },
        created(){
          let data  = localStorage.getItem("todo")
          if (data!=null)
          {
            this.task =data;
          }
        }
      }

  
}
</script>
