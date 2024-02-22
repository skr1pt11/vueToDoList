<template>
  <div v-show="tasks.length > 0" class="tasks">
    <one-task
      v-for="task in tasks"
      :task="task"
      :key="task.id"
      @remove="deleteTask"
    />
  </div>
  <h2 class="h2" v-show="tasks.length === 0"> Список задач пуст ...</h2>
</template>
<script>
import OneTask from "./OneTask.vue";
export default {
  components: {
    OneTask,
  },
  name: "task-list",
  props: {
    tasks: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  emits: ["remove"],
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
.h2{
  margin-top: 60px;
  color: yellow
}
</style>
