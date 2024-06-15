<script setup lang="ts">
import { ref } from "vue";
import OneInfo from "./components/OneInfo.vue"

const propsTitle = ref("発生した乱数");
const rand = Math.round(Math.random() * 100);
const propsContent = ref(rand);
</script>

<template>
  <h1>Props基礎</h1>
  <section>
    <h2>属性に直接記述</h2>
    <!-- リアクティブ変数をpropsとして渡すときはv-bindしないといけない -->
    <OneInfo :title="propsTitle" :content="propsContent" />
  </section>
</template>

<style>
section {
  border: blue 1px solid;
  margin: 10px;
}
</style>