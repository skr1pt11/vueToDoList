<template>
  <div class="newtask">
    <p><strong class="black">Задача: </strong>{{ task.text }}</p>
    <p><strong class="black">Время: </strong>{{ task.time }}</p>
    <p>
      <strong class="black">Статус: </strong>
      <input
      type="checkbox"
      v-model="userCheckbox"
      :true-value="on"
      :false-value="off"
    />
      <span v-if="userCheckbox === on">Решена</span>
      <span v-else>Не решена</span>
    </p>
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
    check: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  emits: ["remove"],
  data() {
    return {
      userCheckbox: this.check,
      on: true,
      off: false,
    };
  },
  watch: {
    check(newValue) {
      this.userCheckbox = newValue;
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
.black {
  color: black;
}
</style>
