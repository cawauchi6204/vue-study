<script setup lang="ts">
import { ref } from "vue";
import OneSection from "./components/OneSection.vue";

const taro = ref("田中太郎")
</script>

<template>
  <section>
    <h2>slotの利用</h2>
    <OneSection :name="taro">
      <p>連絡がつきません</p>
    </OneSection>
  </section>
</template>

<style>
section {
  border: blue 1px solid;
  margin: 10px;
}
</style>