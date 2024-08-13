<template>
  <div class="container">
    <my-input v-model="task" placeholder="Введите задачу ..." />
    <div class="btns">
      <my-button @click="addTask">Добавить задачу</my-button>
      <task-selector v-model="selectedSort" :options="sortOptions" />
      <my-input placeholder="Поиск ..." v-model="keyword" />
    </div>
    <task-list :tasks="sortByKeyword" @remove="deleteTask" v-model="checkboxStatus" :check="checkboxStatus"/>
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
      checkboxStatus: false,
      keyword: "",
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
      localStorage.setItem("task", JSON.stringify(this.tasks));
    },
    addTask() {
      if (this.task === "") return;
      const timeString = new Date().getHours() + ":" + new Date().getMinutes()+ ":" + new Date().getSeconds();
      this.elementForAdd.time = timeString;
      this.elementForAdd.id = Date.now();
      this.elementForAdd.text = this.task;
      this.tasks.push(this.elementForAdd);
      this.task = "";
      localStorage.setItem("task", JSON.stringify(this.tasks));
      this.elementForAdd = {
        time: "",
        id: "",
        text: "",
      };
    },
  },
  computed: {
    sortedTasks() {
      return [...this.tasks].sort((task1, task2) => {
        if (this.selectedSort === "text") {
          return task1[this.selectedSort].localeCompare(
            task2[this.selectedSort]
          );
        }
        return task1[this.selectedSort] - task2[this.selectedSort];
      });
    },
    sortByKeyword() {
      return this.sortedTasks.filter((item) => {
        return item.text.toLowerCase().includes(this.keyword.toLowerCase());
      });
    },
  },
  mounted() {
    let data = localStorage.getItem("task");
    if (data) {
      this.tasks = JSON.parse(data);
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
.btns {
  display: flex;
  justify-content: flex-end;
}
</style>
