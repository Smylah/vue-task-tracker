<template>
  <Header
    :title="title"
    @btn-click="toggleShowTask"
    @info-click="toggleInfo"
    :taskText="showAddTask"
  />
  <div v-show="showInfo">
    <Info />
  </div>
  <div v-show="showAddTask">
    <AddTask @add-task="addTask" />
  </div>
  <Tasks
    @toggle-reminder="toggleReminder"
    @deleteTask="deleteTask"
    :tasks="tasks"
  />
  <router-view> </router-view>
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
import Footer from "./components/Footer.vue";
import Info from "./components/Info.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
    Footer,
    Info,
  },
  data() {
    return {
      title: "Task Tracker",
      tasks: [],
      showAddTask: false,
      showInfo: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id) {
      if (confirm("Are you sure")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    toggleShowTask() {
      this.showAddTask = !this.showAddTask;
    },
    toggleInfo() {
      this.showInfo = !this.showInfo;
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Food Shopping",
        day: "March 3rd at 2:30pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(190, 190, 190);
  padding: 5px 12px;
  max-width: 400px;
  border-radius: 5px;
  margin: auto;
  justify-content: center;
}
</style>
