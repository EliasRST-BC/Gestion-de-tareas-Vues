<template>
  <div class="todo-item">
    <div class="task-info">
      <!-- Título con estilo tachado si la tarea está completada -->
      <h5 :class="{ 'task-completed': completed }">
        {{ title }}
      </h5>
      <!-- Estado de la tarea con colores distintivos -->
      <span :class="completed ? 'status-completed' : 'status-pending'">
        <i :class="completed ? 'bi-check-circle-fill' : 'bi-circle'"></i>
        {{ completed ? 'Completada' : 'Pendiente' }}
      </span>
    </div>

    <!-- Botones de acción con iconos -->
    <div class="action-buttons">
      <button @click="$emit('toggle-completion')" class="btn btn-toggle">
        <i :class="completed ? 'bi-arrow-counterclockwise' : 'bi-check-circle'"></i>
      </button>
      <button @click="$emit('delTodo')" class="btn btn-delete">
        <i class="bi-trash-fill"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    title: String,
    completed: Boolean,
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 8px;
  margin-bottom: 10px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.task-info {
  display: flex;
  flex-direction: column;
}

.task-completed {
  text-decoration: line-through;
  color: #888;
}

.status-completed {
  color: #28a745;
  font-weight: bold;
}

.status-pending {
  color: #ffc107;
  font-weight: bold;
}

.action-buttons .btn {
  background: none;
  border: none;
  cursor: pointer;
  margin-left: 5px;
}

.btn-toggle {
  color: #17a2b8;
}

.btn-toggle:hover {
  color: #138496;
}

.btn-delete {
  color: #dc3545;
}

.btn-delete:hover {
  color: #c82333;
}
</style>

