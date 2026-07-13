<script setup lang="ts">
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'


const id = ref(2);
const textoAdd = ref("");
const headers = ref([{id: 1, texto: "CONSEGUIU!"}])

function adicionarVue() {
  headers.value.push({id: id.value, texto: textoAdd.value})
  id.value++
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld v-for="message in headers" :msg="message.texto" :key="message.id"/>
    </div>
  </header>

  <main>
    <input v-model="textoAdd">
    <button @click="adicionarVue">Novo Vue</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>