<template>
  <div class="wrap">
    <header class="header">
      <h1 class="header__h1">To Do List with Vue</h1>
    </header>
    <div id="app" class="list">
      <h2 class="list__h2">Add some tasks</h2>
      <form class="list__form" action="">
        <input type="text" class="list__input" v-model="newTask" />
        <button class="list__btn" @click.prevent="addNewTask">
          Add task
        </button>
      </form>
      <ul class="list__tasks" v-if="tasks[0]">
        <li v-for="(task, index) in tasks" :key="task">
          {{ task }}
          <i class="far fa-times-circle" @click="removeTask(index)"></i>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      newTask: "",
    };
  },
  methods: {
    addNewTask() {
      this.tasks.push(this.newTask);
      this.newTask = "";
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  background-color: #eee;
}
.wrap {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-height: 70vh;
  min-width: 500px;
  font-family: "Montserrat";
}
.header__h1 {
  height: 100px;
  text-align: center;
  line-height: 100px;
  margin-bottom: 35px;
  background-color: #12ad68;
  color: white;
  border-radius: 15px;
}
.list__h2 {
  height: 60px;
  line-height: 60px;
  text-align: center;
  background-color: #12ad68;
  margin-bottom: 35px;
  color: white;
  border-radius: 15px;
}
.list__form {
  height: 50px;
  text-align: center;
  line-height: 50px;
  margin-bottom: 35px;
}
.list__input {
  height: 30px;
  width: 250px;
  font-family: "Montserrat";
  background-color: #eee;
  border: 1px solid black;
  border-radius: 15px;
  padding-left: 10px;
}
.list__input:focus {
  outline: none;
}
.list__btn {
  height: 30px;
  width: 100px;
  font-family: "Montserrat";
  background-color: #12ad68;
  border: 0;
  border-radius: 15px;
  cursor: pointer;
  color: white;
  font-size: 15px;
  margin-left: 10px;
  transition: 0.1s linear;
}
.list__btn:hover {
  background-color: #127c4c;
}
.list__tasks {
  text-align: center;
  list-style: none;
  font-size: 25px;
  line-height: 40px;
  color: white;
}
li {
  background-color: #12ad68;
  border-radius: 15px;
  height: 40px;
  margin-bottom: 20px;
}
.far {
  cursor: pointer;
}
</style>
