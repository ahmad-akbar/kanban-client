<template>
  <div>
    <h1>{{ message }}</h1>
    <div>
      <Add :fetchTask="fetchTask"></Add>
    </div>
    <div>
      <Update></Update>
    </div>
    <div class="row">
      <Category
        v-for="category in categories" :key="category.id"
        :dataCategory="category"
        :dataTasks="tasks"
        :fetchTask="fetchTask"
      ></Category>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Add from "./add";
import Category from "../components/category";
import Update from "./update"
export default {
  data() {
    return {
      message: "Hello there from home",
      categories: [
        { id: 1, name: "backlog" },
        { id: 2, name: "todo" },
        { id: 3, name: "ongoing" },
        { id: 4, name: "done" },
      ],
      tasks: [],
      showAdd: false
    };
  },
  components: {
    Category,
    Add,
    Update
  },
  methods: {
    fetchTask() {
      axios({
        method: `GET`,
        url: `http://localhost:3000/task`,
        headers: {
          access_token: localStorage.access_token,
        },
      })
        .then((response) => {
          this.tasks = response.data.tasks;
        })
        .catch((err) => {
          console.log(err.message);
        });
    },
    showFormAdd(value) {
      this.showAdd = value
    },
  },
  created() {
    this.fetchTask();
  },
};
</script>

<style>
</style>