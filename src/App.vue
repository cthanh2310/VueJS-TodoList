<template>
  <div>
    <input v-model="newTask" />
    <button @click="addTask" class="btn">Add task</button>
    <TaskComp
      v-for="(task, index) in tasks"
      :key="index"
      :taskData="task"
      :id="index"
      @clicked="deleteTask"
    />
  </div>
</template>
<script>
import TaskComp from './components/TaskComp';
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask: function () {
      this.tasks.push({
        content: this.newTask,
        done: false,
      });
    },
    deleteTask: function (id) {
      console.log('id', id);
      this.tasks.splice(id, 1);
    },
  },
  // watch: {
  //   newTask: function (newValue, oldValue) {
  //     console.log('old: ' + oldValue);
  //     console.log('new: ' + newValue);
  //     console.log('this.newTask', this.newTask);
  //   },
  // },
  components: {
    TaskComp,
  },
};
</script>

<style>
.btn {
  background-color: #fff;
  color: #333;
  border-radius: 20px;
  border: 1px solid #333;
  width: 80px;
}
</style>
