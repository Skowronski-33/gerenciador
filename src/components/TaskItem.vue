<template>
  <li class="task-item" :class="{ completed: task.completed }">
    
    <div class="task-content">
      <input 
        type="checkbox" 
        :checked="task.completed" 
        @change="$emit('toggle-status', task.id)" 
      />
      
      <span class="task-text">
        <strong>{{ taskIndex }}.</strong> {{ task.text }}
      </span>
    </div>

    <button class="delete-btn" @click="$emit('delete-task', task.id)">
      Remover
    </button>
  </li>
</template>

<script setup>
defineProps({
  task: {
    type: Object,
    required: true
  },
  taskIndex: {
    type: Number,
    required: true
  }
})

defineEmits(['toggle-status', 'delete-task'])
</script>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px;
  background-color: #f9f9f9;
  border-radius: 8px;
  margin-bottom: 8px;
  border: 1px solid #eee;
  transition: all 0.3s ease;
}
.task-content {
  display: flex;
  align-items: center;
  gap: 10px;
}
.completed .task-text {
  text-decoration: line-through;
  color: #888;
}
.delete-btn {
  background-color: #ff4c4c;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
}
.delete-btn:hover {
  background-color: #ff1c1c;
}
</style>
