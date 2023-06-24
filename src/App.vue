<script setup>
import { ref } from 'vue';
import Cardcomponent from './components/Cardcomponent.vue';

const users= ref([
  {
    name: "La Chilindrina",
    correo: "lachilli23@gmail.com"
  },
  {
    name: "La Popis",
    correo: "lapopi23@gmail.com"
  }
])

const borrarTarjeta= function(index){
  users.value.splice(index, 1)
}

let name,correo;

const addusers=function(){
 const newUser = {
  name: name,
  correo: correo
 }

 users.value.unshift(newUser)
}

const duplicarTarjeta= function(name,correo){
  const newUser = {
  name: name,
  correo: correo
 }

 users.value.unshift(newUser)
}

</script>

<template>
  <Cardcomponent v-for="(user,index) in users" :key="index" :name="user.name" :correo="user.correo" :index="index" @borrarTarjeta="borrarTarjeta" @duplicarTarjeta="duplicarTarjeta" />
  <div class="mt-3">
    <label>Ingrese su nombre</label>
    <br>
    <input type="text" placeholder="Nombre" v-model="name">
    <br>
    <label>Ingrese su correo</label>
    <br>
    <input type="text" placeholder="Correo" v-model="correo">
    <br>
    <button type="submit" class="mt-2 bg-orange-500 w-20 rounded-lg hover:bg-orange-400 hover:text-white" @click="addusers">Enviar</button>
  </div>
</template>
