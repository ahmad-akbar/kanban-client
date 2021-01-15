<template>
    <div class="card col-3 mt-4" style="width: 18rem;">
        <center>
            <h2>{{ dataCategory.name }}</h2>
        </center>
         <div class="d-flex flex-column">
            <Task v-for="task in filterCategory" :key="task.id" 
            :dataTask="task"
            :fetchTask="fetchTask">
            </Task>
        </div>
    </div>

</template>

<script>
import Task from './task'
export default {
    props: ['dataCategory', 'dataTasks', 'fetchTask'],
  data() {
    return {
    };
  },
  components: {
      Task
  },
  computed: {
      filterCategory(){
          return this.dataTasks.filter(el => el.category === this.dataCategory.name)
      }
  },
};
</script>

<style>
</style>