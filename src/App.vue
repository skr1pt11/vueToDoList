<template>
  <div class="container">
    <div id="newtask">
      <input type="text" placeholder="Task to be done.." v-model.trim="title"/>
      <button id="push" @click="addTask">Add Task</button>
    </div>
    <div id="tasks" v-for="task in tasks" :key="task.id">
      <p><strong>Название задачи: </strong> {{ task.title }}</p>
      <p><strong>Дата публикации: </strong>{{ task.id }}</p>
      <button class ="delete"><img src="../img/trash.jpg" alt="trash"></button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [{ title: "Пример задания", id:  'Дата публикации: ' + new Date().getHours() + ':' + new Date().getMinutes() }],
      title:''
    }
  },
  methods: {
    addTask(){
      let obj = {
      title: this.title,
      id: new Date().getHours() + ':' + new Date().getMinutes()
      }
      if(this.title.length === 0) return
      this.title = ''
      this.tasks.push(obj)
    }
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
#tasks {
  background-color: #ffffff;
  padding: 30px 20px;
  margin-top: 60px;
  border-radius: 10px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
  width: 100%;
  position: relative;
}
.task {
  background-color: #ffffff;
  height: 50px;
  padding: 5px 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 2px solid #d1d3d4;
  cursor: pointer;
}
.task span {
  font-family: "Poppins", sans-serif;
  font-size: 15px;
  font-weight: 400;
}
.completed {
  text-decoration: line-through;
}
</style>
