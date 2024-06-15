<script setup lang="ts">
import { ref, watch, watchEffect } from 'vue';

// メモ computedは非同期処理には向いていない

type Cocktail = {
  id: number;
  name: string;
  price: number;
}

const cocktailDataListInit: Cocktail[] = [
  { id: 2345, name: "ホワイト・レディ", price: 1200 },
  { id: 4412, name: "ブルーハワイ", price: 1500 },
  { id: 6789, name: "ニューヨーク", price: 1700 },
  { id: 3439, name: "マティーニ", price: 1900 },
]
const selectedCocktail = ref(cocktailDataListInit[0])
setInterval(() => {
  const rand = Math.floor(Math.random() * cocktailDataListInit.length)
  const randomCocktail = cocktailDataListInit[rand]
  selectedCocktail.value = randomCocktail
}, 1000)
watch([selectedCocktail], () => {
  console.log('selectedCocktail.value:', selectedCocktail.value)
})
watchEffect(() => {
  console.log('selectedCocktail.value:', selectedCocktail.value)
})
</script>

<template>
  <section>
    <h1>ランダムカクテル</h1>
    <p>今日のおすすめは「{{ selectedCocktail.name }} {{ selectedCocktail.price }}円」です。</p>
  </section>
</template>