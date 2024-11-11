<template>
  <div class="add-task-container">
    <h1>Añadir Tarea</h1>
    <div class="input-group">
      <input 
        v-model="newTask" 
        @keyup.enter="addTask" 
        placeholder="Añadir nueva tarea" 
        class="task-input"
      />
      <button @click="addTask" class="add-button styled-button">
        <i class="bi bi-plus-circle"></i> Añadir
      </button>
    </div>
    <!-- Botón para mostrar tareas extraídas de la API -->
    <button @click="showTasksApi" class="styled-button">Mostrar Tareas de la API</button>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      newTask: ""
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        const newTask = {
          todo: this.newTask,
          completed: false,
          id: Date.now()
        };
        this.$emit('taskAdded', newTask);
        this.newTask = "";
      }
    },
    showTasksApi() {
      this.$emit('toggleApiTasks'); // Emitimos el evento para mostrar las tareas de la API
    }
  }
};
</script>
