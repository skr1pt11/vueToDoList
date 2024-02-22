<template>
  <div class="tasks">
    <one-task
      v-for="task in tasks"
      :task="task"
      :key="task.id"
      @remove="deleteTask"
    />
  </div>
</template>
<script>
import OneTask from "./OneTask.vue";
export default {
  name: "task-list",
  components: {
    OneTask,
  },
  props: {
    tasks: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  methods: {
    deleteTask(task) {
      this.$emit("remove", task);
    },
  },
};
</script>
<style scoped>
.tasks {
  background-color: #ffffff;
  padding: 30px 20px;
  margin-top: 60px;
  border-radius: 10px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
  width: 100%;
  position: relative;
}
</style>
