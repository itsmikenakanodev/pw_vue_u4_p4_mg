<template>
  <div class="container">
    <label for="">Id:</label>
    <input type="text" v-model="id" />
    <button @click="eliminarEstudiante">Eliminar</button>
    <label v-if="nombre" for="">Se elimino el estudiante:  "{{ this.nombre }}" con cedula: "{{this.cedula}}"</label>
  </div>
</template>

<script>
import { eliminarEstudianteFachada } from "../helpers/EstudianteCliente";

export default {
  data() {
    return {
      id: null,
      nombre: null,
      cedula: null
    };
  },
  methods: {
    async eliminarEstudiante() {
      const data = await eliminarEstudianteFachada(this.id);
      this.nombre = data.nombre;
      this.cedula = data.cedula;
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 120px;
  margin-left: 500px;
  padding: 20px;
  max-width: 500px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: rgba(255, 255, 255, 0.8); /* Fondo con opacidad para el efecto de desenfoque */
  backdrop-filter: blur(4px);
}

label {
  width: 400px;
  margin-bottom: 5px;
  font-weight: 750;
  color:#1d61ff;
  text-align: left;
  text-shadow: -1px -1px 0 #ffffffd0, 1px -1px 0 #fff, -1px 1px 0 #fff, 1px 1px 0 #fff;
}

input {

  width: 400px;
  padding: 8px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: border-color 0.3s ease;
}

button {

  width: 400px;
  padding: 10px;
  background-color: #85f0e7;
  color: #070707;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  font-weight: bold;
}

input:hover,
button:hover {
  border-color: #007bff;
}

input:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 3px rgba(0, 123, 255, 0.5);
}

button:active {
  background-color: #0056b3;
}
</style>