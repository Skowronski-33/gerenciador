<template>
  <div class="app-container">
    <h1>Gerenciador de Tarefas</h1>
    
    <form @submit.prevent="addTask" class="task-form">
      <input 
        type="text" 
        v-model="newTaskText" 
        placeholder="O que precisa ser feito?" 
        required
      />
      <button type="submit" class="add-btn">Adicionar Tarefa</button>
    </form>

    <div class="task-board">
      <p v-if="tasks.length === 0" class="empty-message">
        🎉 Nenhuma tarefa pendente. Aproveite o seu dia!
      </p>

      <ul v-else class="task-list">
        <TaskItem 
          v-for="(task, index) in tasks" 
          :key="task.id"
          :task="task"
          :taskIndex="index + 1"
          @toggle-status="toggleTaskStatus"
          @delete-task="deleteTask"
        />
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TaskItem from './components/TaskItem.vue'

const newTaskText = ref('')

const tasks = ref([])

function addTask() {
  if (newTaskText.value.trim() === '') return
  
  const newTask = {
    id: Date.now(),
    text: newTaskText.value,
    completed: false
  }
  
  tasks.value.push(newTask)
  newTaskText.value = ''
}

function toggleTaskStatus(taskId) {
  const task = tasks.value.find(t => t.id === taskId)
  if (task) {
    task.completed = !task.completed
  }
}

function deleteTask(taskId) {
  tasks.value = tasks.value.filter(t => t.id !== taskId)
}
</script>

<style>
body {
  background-color: #f3f4f6;
  margin: 0;
}
.app-container {
  max-width: 600px;
  margin: 40px auto;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}
h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}
.task-form {
  display: flex;
  gap: 10px;
  margin-bottom: 25px;
}
.task-form input {
  flex: 1;
  padding: 10px 15px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 16px;
}
.add-btn {
  padding: 10px 20px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 6px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.2s;
}
.add-btn:hover {
  background-color: #33a06f;
}
.empty-message {
  text-align: center;
  color: #666;
  font-style: italic;
}
.task-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
</style>
