<template>
  <div class="newtask">
    <p><strong class="black">Задача: </strong>{{ task.text }}</p>
    <p><strong class="black">Время: </strong>{{ task.time }}</p>
    <p><strong class="black">Выполнена: </strong>{{ task.status }}</p>
    <my-button @click="$emit('remove', task)">Удалить</my-button>
  </div>
</template>
<script>
export default {
  name: "one-task",
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style scoped>
.newtask {
  margin-bottom: 15px;
  position: relative;
  background-color: #73afa0;
  padding: 30px 20px;
  border-radius: 5px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
  height: 150px;
}
.newtask p {
  color: whitesmoke;
}
.black{
  color: black;
}
</style>
