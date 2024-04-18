
<script setup>
const mensaje ='Vue diámico';
const styleColor = {color: 'blue'};
const arraycolor = ['red','blue','green'];
const activo = true;
const arrayFrutas = ['🍇', '🍉', '🍌','🍓'];
const arrayFrutas2 = [
  {
    nombre:'Manzana',
    precio: 100,
    descripcion: 'Una Manzana'
  },
  {
    nombre:'Pera',
    precio: 300,
    descripcion: 'Una Pera'
  },
  {
    nombre:'Banana',
    precio: 200,
    descripcion: 'Una Banana'
  }
]
</script>

<template>
  <h1>Hola {{mensaje.toUpperCase() }}!</h1>
  <!--los : es la abrebiacion del v-bind-->
  <h2 :style="`color:${arraycolor[1]}`">Soy azul</h2>
  <h2>
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h2>
  <p v-if="activo">Estoy activo</p>
  <p v-else>Estoy inactivo</p>

  <h2 v-show="activo">Estoy activo v-show</h2>

  <ul>
    <li v-for="fruta in arrayFrutas2" :key="fruta.nombre">{{ fruta.nombre }} -- ${{ fruta.precio }} -- {{ fruta.descripcion }}</li>
  </ul>


  <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index">{{index}} - {{ fruta }}</li>
  </ul>
</template>

<style>
h1{
  color: red;
}
</style>