<template>
  <div class="task-comp">
    <label class="label">
      <input type="checkbox" :checked="taskData.done" @click="onChecked" />
      <span v-bind:class="{ done: taskData.done }">
        {{ taskData.content }}
      </span>
    </label>
    <button class="btn" @click="handleDelete">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'TaskComp',
  props: ['taskData', 'clicked', 'id'],
  methods: {
    onChecked() {
      this.$props.taskData.done = !this.$props.taskData.done;
    },
    handleDelete() {
      console.log('this.props', this.$props.id);
      this.$emit('clicked', this.$props.id);
    },
  },
};
</script>

<style scoped>
.label {
  margin-right: 8px;
}
.btn {
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}
</style>
