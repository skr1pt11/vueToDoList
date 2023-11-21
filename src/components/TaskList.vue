<template>
  <div id="tasks" v-for="task in tasks" :key="task.id">
    <p><strong>Название задачи: </strong> {{ task.title }}</p>
    <p><strong>Дата публикации: </strong>{{ task.time }}</p>
    <!-- <button class="delete"><img src="../img/trash.jpg" alt="trash" /></button> -->
  </div>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
#tasks{
    background-color: #ffffff;
    padding: 30px 20px;
    margin-top: 60px;
    border-radius: 10px;
    box-shadow: 0 15px 30px rgba(0,0,0,0.3);
    width: 100%;
    position: relative;
}
</style>
