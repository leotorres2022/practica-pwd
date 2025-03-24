<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()
const nombre = ref ("")
const email = ref ("")
const password = ref ("")
const nacim = ref ("")


function GuardarDatos(){
  const edadCal = CalcularEdad()

  let Usuario ={
    nombre:nombre.value,
    email:email.value,
    password:password.value,
    nacim:nacim.value,
    edad:edadCal
  }

  const datosUsuario = `
    Nombre: ${Usuario.nombre}
    Email: ${Usuario.email}
    Password: ${Usuario.password}
    Edad:${Usuario.edad}
   
  `;

    alert ( datosUsuario)
    alert("Usuario creado Correcto")

   nombre.value=""
   email.value=""
   password.value=""
   nacim.value=""
 

}

function CalcularEdad(){
  const fechaNacimientoDate = new Date(nacim.value);
  const hoy = new Date ()
     let edad =  hoy.getFullYear()- fechaNacimientoDate.getFullYear()
    console.log (edad)
    return edad
}

</script>

<template>
  <form @submit.prevent="">
    <h1 >{{ msg }}</h1>

<div class="form">
  <label >Ingrese el  Nombre de Usuario </label>
  <input type="text" v-model="nombre"></input><br>
  <label >Ingrese el  Mail   </label>
  <input type="email" v-model="email"></input><br>
  <label >Ingrese el Password  </label>
  <input type="password" v-model="password"></input> <br>
  <label >Ingrese la Fecha de Nacimiento   </label>
  <input type="date" v-model="nacim" id="nacimiento"></input> <br>
  <button type="button" @click="GuardarDatos"> Guardar  </button>
 
  </div>
  <div>
    <p>
      {{ nombre }} <br>
      {{ email }} <br>
      {{ password }} <br>
      {{ nacim }} <br>
    </p>
  </div>
  

  </form>
 
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

</style>
