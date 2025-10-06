<script lang="ts" setup>
import { ref } from "vue";

const header = ref("Languages List");
const items = ["berber", "french", "arabic", "english", "deutsch", "spanish"];
const selectedLanguage = ref("Aqui aparecera la lengua seleccionada.");
const message = "hola";

var modelx = ref(0);
function update() {
  console.log(
    "Se ha puslado el boton de incremento  " + modelx.value + "  veces"
  );
  alert(modelx.value++);
}
</script>
<style>
header,
footer {
  background-color: lightblue;
  text-align: center;
}
h2 {
  display: flex;
  justify-content: left;
}
h4 {
  padding: 30.4px;
}
h1 {
  padding: 24px;
}
</style>
<template>
  <body>
    <header>
      <h1>Ejercicios VueJs</h1>
    </header>
    <main>
      <h2>{{ header }}</h2>

      <select v-model="selectedLanguage">
        <option value="" selected>Idioma</option>
        <!--no funciona no aparece idioma por defecto¿?-->
        <option v-for="item in items" :key="item" :value="item">
          {{ item }}
        </option>
      </select>
      <p v-if="selectedLanguage">Idioma seleccionado: {{ selectedLanguage }}</p>
    </main>

    <footer>
      <h4>VueJs</h4>
    </footer>
  </body>
  <p>
    La palabra '{{ message.toUpperCase() }}' revertida es: '{{
      message.split("").reverse().join("").toUpperCase()
    }}' y consta de {{ message.length }} letras.
  </p>
  <input v-model="modelx" />
  <div>Se ha pulsado el contador: {{ modelx }} veces</div>
  <button @click="update">Increment</button>

  <p hidden="true">This is hidden from screen readers.</p>
</template>
