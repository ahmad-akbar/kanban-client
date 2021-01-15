<template>
<div class="container">
    <form>
  <div class="form-group row">
    <label for="inputEmail3" class="col-sm-2 col-form-label">Title</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" v-model="addTitle" placeholder="Title">
    </div>
  </div>
  <div class="form-group row">
    <label for="inputPassword3" class="col-sm-2 col-form-label">Description</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" v-model="addDescription" placeholder="Description">
    </div>
  </div>
  <div class="form-group row">
    <div class="col-sm-10">
      <button type="submit" class="btn btn-primary" @click.prevent="addTask()">Add new task</button>
    </div>
  </div>
</form>
</div>
</template>

<script>
import axios from 'axios'
export default {
    props: ['fetchTask'],
    data(){
        return{
            addTitle: "",
            addDescription: ""
        }
    },
    methods: {
        addTask(){
            axios({
                method: `POST`,
                url: `http://localhost:3000/task`,
                headers: {
                access_token: localStorage.access_token
                },
                data: {
                    title: this.addTitle,
                    description: this.addDescription,
                    category: 'backlog'
                }
            })
            .then( response => {
                this.fetchTask()
            })
            .catch( err => {
            console.log(err.message);
            })
        }
    }
}
</script>

<style>

</style>