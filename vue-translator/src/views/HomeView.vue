<script setup>
import { ref } from "vue";

const userInput = ref("");
const transResult = ref("");

const translate = () => {
  console.log(userInput.value);

  fetch(`https://api.mymemory.translated.net/get?q=${userInput.value}&langpair=en|cs`)
  .then( response => response.json())
  .then( data => {
    // tady mame odpoved ze serveru v promenne data
    console.log(data);
    transResult.value = data.responseData.translatedText
  });
}

</script>

<template>
  <main>
    <input type="text" v-model="userInput" placeholder="Text for translation..." >
    <button @click="translate">Translate</button>
    <div>
        {{ userInput }}
        -->
        {{ transResult }}
    </div>
  </main>
</template>

<style>
  input {
    color: blueviolet;
  }
</style>
