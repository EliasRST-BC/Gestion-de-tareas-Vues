<template>
  <div>
    <h2>Lista de Tareas</h2>
    <ul>
      <!-- Mostrar las tareas -->
      <li v-for="task in tasks" :key="task.id" class="task-item">
        <span :class="{ completed: task.completed }">{{ task.todo }}</span>
        <div>
          <!-- Botón para marcar/desmarcar tarea como completada -->
          <button @click="$emit('toggle-completion', task)" class="styled-button">
            <i :class="task.completed ? 'bi-arrow-counterclockwise' : 'bi-check-circle'"></i>
          </button>
          <!-- Botón para eliminar la tarea -->
          <button @click="$emit('delTodo', task)" class="styled-button delete-button">
            <i class="bi-trash-fill"></i>
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TaskList',
  props: {
    tasks: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
}

.completed {
  text-decoration: line-through;
  color: gray;
}

.styled-button {
  background: none;
  border: none;
  cursor: pointer;
  margin-left: 5px;
  color: #17a2b8;
}
.styled-button i {
  font-size: 1.2em;
  color: #007bff;
}

.delete-button i {
  color: #dc3545; /* Color rojo para el icono de eliminar */
}

.styled-button:hover i,
.delete-button:hover i {
  color: white; /* Color de los iconos cuando se pasa el ratón */
}
</style>
