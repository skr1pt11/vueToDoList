<template>
  <div id="newtask">
    <input type="text" placeholder="Task to be done.." v-model.trim="task.title" />
    <button id="push" @click="addTask">Add Task</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      task: {
        title: "",
      },
    };
  },
  methods: {
    addTask() {
      if (this.task.title.length === 0) return;
      this.task.id = new Date().getTime();
      this.task.time = new Date().getHours() + ":" + new Date().getMinutes();
      this.$emit("create", this.task);
      this.task = {
        title: "",
      };
    },
  },
};
</script>

<style scoped>
#newtask {
  position: relative;
  background-color: #ffffff;
  padding: 30px 20px;
  border-radius: 5px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
}
#newtask input {
  width: 70%;
  width: 70%;
  height: 45px;
  font-family: "Poppins", sans-serif;
  font-size: 15px;
  border: 2px solid #d1d3d4;
  padding: 12px;
  color: #111111;
  font-weight: 500;
  position: relative;
  border-radius: 5px;
}
#newtask input:focus {
  outline: none;
  border-color: #8052ec;
}

#newtask button {
  position: relative;
  float: right;
  width: 20%;
  height: 45px;
  border-radius: 5px;
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  font-size: 16px;
  background-color: #8052ec;
  border: none;
  color: #ffffff;
  cursor: pointer;
  outline: none;
}
</style>
