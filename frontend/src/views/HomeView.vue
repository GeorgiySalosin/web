<script setup lang="ts">
import axios from 'axios';
import { onMounted, ref } from 'vue';

let clicks = ref<number>(0)

let otchislen = ref<boolean | number>(true)

let login = ref<string>("")
let password = ref<string>("")

let color = ref<"red" | "yellow" | "green">("green")

let url = ref<string>("")

let fun = (it: number) => {
  clicks.value += it
  otchislen.value = !otchislen.value
}

let getBooks = async () => {
    try {
        const res = await axios.get("https://stephen-king-api.onrender.com/api/books")
        console.log(res)
    } catch (err) {
        console.log(err)
    }
}

onMounted(() => {
    getBooks()
})
</script>

<template>
  <h1>Вы сделали это!</h1>

  <button @click="$router.push('/auth')">Авторизация</button>

  <input v-model="url" placeholder="Введите ссылку на фото" type="text">
  <img :src="url">

  <input v-model="login" type="text">
  <input v-model="password" type="password">
  <button>Войти</button>
  <p>Логин: {{ login }}</p>
  <p>Пароль: {{ password }}</p>

  <p v-if="otchislen">Отчислен</p>
  <!-- <p v-else>Пока учится</p> -->
  <p v-show="otchislen">Отчислен</p>
  <p>Накликали: {{ clicks }}</p>
  <button @click="fun(i)" v-for="i in 100">Привет {{ i }}</button>
</template>

<style scoped></style>
