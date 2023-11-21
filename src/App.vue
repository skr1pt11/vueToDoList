<template>
  <div class="container">
    <task-form @create="addTask"/>
    <task-list :tasks="tasks" />
  </div>
</template>

<script>
import TaskForm from "./components/TaskForm.vue";
import TaskList from "./components/TaskList.vue";
export default {
  components: {
    TaskForm,
    TaskList,
  },
  data() {
    return {
      tasks: [
        {
          title: "Пример задания",
          time:
            "Дата публикации: " +
            new Date().getHours() +
            ":" +
            new Date().getMinutes(),
          id: new Date().getTime(),
        },
      ],
    };
  },
  methods: {
    addTask(task) {
      this.tasks.push(task)
    },
  },
};
</script>

<style>
*,
*:before,
*:after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  height: 100vh;
  background: linear-gradient(135deg, #8052ec, #d161ff);
}
.container {
  width: 40%;
  min-width: 450px;
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  top: 30px;
  padding: 30px 40px;
}
.completed{
    text-decoration: line-through;
}
</style>
