<script setup lang="ts">
import { ref } from 'vue';

const inputNameModel = ref("双方向")
</script>

<template>
  <section>
    <!-- v-model = v-bindとv-on:inputの組み合わせ -->
    <input type="text" v-model="inputNameModel">
    <p>{{ inputNameModel }}</p>
  </section>
</template>