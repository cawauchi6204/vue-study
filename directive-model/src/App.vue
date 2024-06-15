<script setup lang="ts">
import { computed, ref } from 'vue';

const cocktailDataListInit = [
  { id: 2345, name: "ホワイト・レディ", price: 1200 },
  { id: 4412, name: "ブルーハワイ", price: 1500 },
  { id: 6789, name: "ニューヨーク", price: 1700 },
  { id: 3439, name: "マティーニ", price: 1900 },
]
const cocktailDataList = ref(cocktailDataListInit)
const cocktail1500 = computed(
  () => {
    const newList = cocktailDataList.value.filter(
      (cocktailItem) => {
        return cocktailItem.price == 1500
      }
    )
    return newList
  }
)
</script>

<template>
  <section>すべてのカクテルリスト
    <ul>
      <li v-for="cocktailData in cocktailDataList" v-bind:key="cocktailData.id">
        {{ cocktailData.id }}: {{ cocktailData.name }}: {{ cocktailData.price }}円
      </li>
    </ul>
  </section>
  <section>
    値段が1500円のカクテルリスト
    <ul>
      <li v-for="cocktail in cocktail1500" v-bind:key="cocktail.id">
        {{ cocktail.id }}: {{ cocktail.name }}: {{ cocktail.price }}円
      </li>
    </ul>
  </section>
</template>