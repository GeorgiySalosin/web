<script setup lang="ts">
import { ref } from 'vue';

let clicks = ref(0)

let fun = () => {
  clicks.value += 1
}
</script>

<template>
  <h1>Вы сделали это!</h1>
  <p>Накликали: {{ clicks }}</p>
  <button @click="fun" v-for="i in 100">Привет {{ i }}</button>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
</template>

<style scoped></style>
