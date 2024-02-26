<template>
  <div class="container">
    <my-input v-model="task" placeholder="Введите задачу ..."/>
    <div class="btns">
      <my-button @click="addTask">Добавить задачу</my-button>
      <task-selector v-model="selectedSort" :options="sortOptions" />
      <my-input placeholder="Поиск ..." v-model="keyword"/>
    </div>
    <task-list :tasks="tasks" @remove="deleteTask" />
  </div>
</template>

<script>
import TaskList from "./components/TaskList.vue";
export default {
  name: "app",
  components: {
    TaskList,
  },
  data() {
    return {
      keyword: '',
      selectedSort: "",
      sortOptions: [
        {
          value: "text",
          name: "По названию",
        },
        {
          value: "id",
          name: "По дате",
        },
      ],
      task: "",
      elementForAdd: {},
      tasks: [],
    };
  },
  methods: {
    deleteTask(task) {
      const index = this.tasks.indexOf(task);
      if (index === -1) {
        return;
      }
      this.tasks.splice(index, 1);
    },
    addTask() {
      if (this.task === "") return;
      const timeString = new Date().getHours() + ":" + new Date().getMinutes();
      this.elementForAdd.time = timeString;
      this.elementForAdd.id = Date.now();
      this.elementForAdd.text = this.task;
      this.elementForAdd.status = "Нет";
      this.tasks.push(this.elementForAdd);
      this.task = "";
      this.elementForAdd = {
        time: "",
        id: "",
        text: "",
        status: "",
      };
    },
  },
  watch: {
    selectedSort(newValue) {
      this.tasks.sort((task1, task2) => {
        if(newValue === 'text'){
          return task1[newValue].localeCompare(task2[newValue]);
        }
        return task1[newValue] - task2[newValue]
      });
    },
  },
  computed:{
    sortByKeyword(){
      return this.task.filter((item)=>{
        return item.name.toLowerCase().includes(this.keyword.toLowerCase()).sort(selectedSort())
      })
    }
  }
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
.btns {
  display: flex;
  justify-content: flex-end;
}
</style>
