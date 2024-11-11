<template>
  <div>
    <button
      class="btn"
      :class="showTasks ? 'btn-success' : 'btn-outline-primary'"
      @click="toggleView"
    >
      <i class="bi" :class="showTasks ? 'bi-eye-slash' : 'bi-eye'"></i>
      {{ showTasks ? 'Ocultar Vista Combinada' : 'Vista Combinada' }}
    </button>

    <div v-if="showTasks">
      <!-- Añadir Tarea -->
      <AddTask @taskAdded="addNewTask" />
      
      <!-- Lista de Tareas -->
      <TaskList 
        :tasks="tasks" 
        @toggle-completion="toggleTaskCompletion" 
        @delTodo="deleteTask" 
      />
    </div>
  </div>
</template>

<script>
import AddTask from '@/views/AddTask.vue';
import TaskList from '@/views/TaskList.vue';
import axios from 'axios';

export default {
  name: 'CombinedView',
  components: { AddTask, TaskList },
  data() {
    return {
      tasks: [],  // Lista de tareas
      showTasks: false
    };
  },
  methods: {
    toggleView() {
      this.showTasks = !this.showTasks;
      if (this.showTasks && this.tasks.length === 0) {
        this.fetchTasks();  // Cargar tareas de la API si es necesario
      }
    },
    async fetchTasks() {
      try {
        const response = await axios.get('https://dummyjson.com/todos');
        this.tasks = response.data.todos;
      } catch (error) {
        console.error("Error al cargar las tareas:", error);
      }
    },
    addNewTask(task) {
      this.tasks.unshift(task);  // Agregar tarea a la lista de tareas
    },
    toggleTaskCompletion(task) {
      const index = this.tasks.findIndex(t => t.id === task.id);
      if (index !== -1) {
        this.tasks[index].completed = !this.tasks[index].completed;
        // Actualizar estado en la API si es necesario
      }
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter(t => t.id !== task.id);
      // Eliminar tarea de la API si es necesario
    }
  },
  mounted() {
    this.fetchTasks();  // Cargar tareas al montar el componente
  }
};
</script>
