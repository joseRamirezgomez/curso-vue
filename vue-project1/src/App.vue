<script setup>
const mensaje = 'Vue diámico';
const styleColor = { color: 'blue' };
const arraycolor = ['red', 'blue', 'green'];
const activo = true;
const arrayFrutas = ['🍇', '🍉', '🍌', '🍓'];
const arrayFrutas2 = [
  {
    nombre: 'Manzana',
    precio: 100,
    descripcion: 'Una Manzana',
    stock: 10,
  },
  {
    nombre: 'Pera',
    precio: 300,
    descripcion: 'Una Pera',
    stock: 0,
  },
  {
    nombre: 'Banana',
    precio: 200,
    descripcion: 'Una Banana',
    stock: 20,
  }
];

const objetoFruta = {
  nombre: 'Pera',
  precio: 300,
  descripcion: 'Una Pera'
};

// metodos -methods
const handleClick = (message) => {
  console.log(message);
};
</script>

<template>
  <h1>Hola {{ mensaje.toUpperCase() }}!</h1>
  <!--los : es la abrebiacion del v-bind-->
  <h2 :style="`color:${arraycolor[1]}`">Soy azul</h2>
  <h2>
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h2>
  <p v-if="activo">Estoy activo</p>
  <p v-else>Estoy inactivo</p>

  <h2 v-show="activo">Estoy activo v-show</h2>

  <ul>
    <li v-for="fruta in arrayFrutas2" :key="fruta.nombre">{{ fruta.nombre }} -- ${{ fruta.precio }} -- {{
      fruta.descripcion }}</li>
  </ul>


  <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index">{{ index }} - {{ fruta }}</li>
  </ul>

  <!-- recorriendo objetos -->
  <ul>
    <li v-for="(value, propiedad) in objetoFruta" :key="value">
      {{ propiedad }} : {{ value }}
    </li>
  </ul>

  <h2>v-for y v-if</h2>
  <!-- recorriendo elementos de forma optima con v-for y v-if -->

  <ul>
    <template v-for="item in arrayFrutas2" :key="item.nombre">
      <li v-if="item.stock > 0">
        {{ item.nombre }} - {{ item.precio }}

      </li>
    </template>
  </ul>

  <!-- v-on:click -->

  <button v-on:click.right.prevent="handleClick('Texto right')">Activame right</button>
  <button @click="handleClick('Texto left')">Activame left</button>
  <button @click.middle="handleClick('Texto middle')">Activame middle</button>


</template>

<style>
h1 {
  color: red;
}
</style>