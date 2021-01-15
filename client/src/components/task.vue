<template>
  <div class="card" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ dataTask.title }}</h5>
      <p class="card-text"> {{ dataTask.description}} </p>
      <button type="submit" class="btn btn-primary" @click="deleteTask(dataTask.id)">Delete</button>
      <button type="submit" class="btn btn-primary" >Update</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  props:['dataTask','fetchTask'],
  data(){
    return{
    }
  },
  methods:{
    deleteTask(id){
      axios({
        method: `DELETE`,
        url:`http://localhost:3000/task/${id}`,
        headers: {
          access_token: localStorage.access_token
        }
      })
      .then( response => [
        this.fetchTask()
      ])
      .catch( err => {
        console.log(err.message);
      })
    }
  },

  created(){
    // this.fetchTask()
  }
};
</script> 

<style>
</style>