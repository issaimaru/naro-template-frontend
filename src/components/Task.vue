<script setup lang="ts">
import { ref } from 'vue'

interface Task {
  name: string
  status: string
}

const Task = ref<Task[]>([
  { name: 'テックちゃんとデート', status: 'incomplete' },
  { name: 'ゆうにぼを見る', status: 'complete' }
])
const newTaskName = ref('')
const newTaskStatus = ref('')

const addTask = () => {
  Task.value.push({ name: newTaskName.value, status: newTaskStatus.value })
}
const removeTask = (item: Task) => {
  Task.value = Task.value.filter(i => i !== item)
}
</script>

<template>
  <div>
    <div>TaskList</div>
    <ul>
        <li v-for="item in Task" :key="item.name">
        <div>名前: {{ item.name }}</div>
        <div>ステータス: {{ item.status }}</div>
        <button @click="removeTask(item)">削除</button>
      </li>
    </ul>
    <div>
      <label>
        タスク
        <input v-model="newTaskName" type="text" />
      </label>
      <label>
        ステータス
        <input v-model="newTaskStatus" type="text" />
      </label>
      <button @click="addTask">追加</button>
      </div>
  </div>
</template>

<style></style>