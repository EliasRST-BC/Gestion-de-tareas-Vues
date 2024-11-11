<template>
  <div class="hello">
    <h1 class="title">Bienvenido a la app de Gestión de Tareas!</h1>
    <p class="description">
      Esta aplicación te permite gestionar tus tareas de manera eficiente. Puedes añadir nuevas tareas manualmente o extraerlas desde una API.
    </p>
    <h2 class="section-title">Secciones de la Aplicación</h2>
    <h3 class="sections">
      Añadir Tarea: Permite ingresar nuevas tareas manualmente.<br />
      Lista de Tareas: Muestra todas las tareas extraídas desde la API, permitiendo marcarlas como completadas o eliminarlas.<br />
      Vista Combinada: Combina las funcionalidades de añadir tareas manualmente y ver las tareas de la API al mismo tiempo.
    </h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
.hello {
  text-align: center;
  padding: 20px;
  background: linear-gradient(135deg, #f5f7fa, #c3cfe2);
  border-radius: 15px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 2.5em;
  font-weight: bold;
  background: linear-gradient(90deg, #ff8a00, #e52e71, #9b00ff);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  animation: gradient 3s ease-in-out infinite;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}

.description {
  font-size: 1.2em;
  margin-top: 15px;
  color: #4a4a4a;
  animation: fadeIn 2s;
}

.section-title {
  font-size: 1.8em;
  color: #3498db;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
  margin-top: 30px;
  transition: transform 0.3s;
}

.section-title:hover {
  transform: scale(1.05);
}

.sections {
  font-size: 1.1em;
  line-height: 1.6;
  color: #2c3e50;
  margin-top: 20px;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
