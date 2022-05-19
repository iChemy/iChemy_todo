<script setup>
import { ref } from "vue";

//未完了のタスクの格納
const tasks = ref([{ name: "todoリストを作る", state: -1 }]);
//入力されたタスク
const newTask = ref([""]);
//入力したのをボタンを押して追加する機能
const addTask = () => {
  if (newTask.value !== "") {
    tasks.value.push({ name: newTask.value, state: -1 });
    newTask.value = "";
  }
};
</script>
<template>
  <div class="undone"><h3>I have to do!!</h3></div>
  <div v-for="task in tasks" :key="task.name">
    <div class="task">
      <div v-if="task.state < 0" :class="name">
        未完タスク: {{ task.name }}
        <button @click="task.state += 2">完了!!</button>
      </div>
    </div>
  </div>
  <div class="done"><h3>I am done!!</h3></div>
  <div v-for="task in tasks" :key="task.name">
    <div class="task">
      <div v-if="task.state > 0" :class="name">完了タスク: {{ task.name }}</div>
    </div>
  </div>
  <div>
    <label>
      タスク
      <input v-model="newTask" type="text" />
    </label>
    <button @click="addTask">add your task</button>
  </div>
</template>

<style>
.undone {
  color: aqua;
  font-size: large;
}
.done {
  color: blue;
  font-size: large;
}
</style>
