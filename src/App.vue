<template>
  <div class="form-container">
    <h2>Formulario Básico</h2>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="name">Nombre:</label>
        <input type="text" id="name" v-model="form.name" required />
      </div>

      <div>
        <label for="email">Correo:</label>
        <input type="email" id="email" v-model="form.email" required />
      </div>

      <div>
        <label for="message">Mensaje:</label>
        <textarea id="message" v-model="form.message"></textarea>
      </div>

      <button type="submit">Enviar</button>
    </form>

    <div v-if="submitted">
      <h3>Datos enviados:</h3>
      <p>Nombre: {{ form.name }}</p>
      <p>Correo: {{ form.email }}</p>
      <p>Mensaje: {{ form.message }}</p>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  name: '',
  email: '',
  message: ''
})

const submitted = ref(false)

function handleSubmit() {
  submitted.value = true
  console.log('Formulario enviado:', form)
}
</script>

<style scoped>
.form-container {
  max-width: 400px;
  margin: auto;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}

div {
  margin-bottom: 10px;
}

label {
  display: block;
  margin-bottom: 4px;
}

input, textarea {
  width: 100%;
  padding: 6px;
  box-sizing: border-box;
}

button {
  padding: 8px 12px;
  cursor: pointer;
}
</style>
