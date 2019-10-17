<template>
  <div id="app">
   <h2 class="bg-primary text-white text-center p-2">{{name}} To Do List</h2>
   <div class="container-fluid p4">
     <div class="row">
       <div class="col font-weight-bold">
         Task
       </div>
       <div class="col-2 font-weight-bold">
        
         Done
       </div>
     </div>
     <div class="row" v-for="t in task" v-bind:key="t.action">
         <div class="col">
         {{t.action}}
       </div>
       <div class="col-2">
          <input type="checkbox" v-model="t.done" class="form-check-input"/>
         {{t.done}}
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
      ]
    }
  }
  
}
</script>
