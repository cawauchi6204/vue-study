<script setup lang="ts">
import { ref } from "vue";
import Input from "./components/Input.vue";
import Radio from "./components/Radio.vue";
import Select from "./components/Select.vue";

const currentComp = ref(Input);
const currentCompName = ref("Input");

const compList = [Input, Radio, Select]
const compNameList: string[] = ["Input", "Radio", "Select"]

let currentCompIndex = 0;
const switchComp = () => {
  currentCompIndex++;
  if (currentCompIndex >= compList.length) {
    currentCompIndex = 0;
  }

  currentComp.value = compList[currentCompIndex];
  currentCompName.value = compNameList[currentCompIndex];
}
</script>

<template>
  <p>コンポーネント名: {{ currentCompName }}</p>
  <!-- KeepAliveがあるとそれまでの入力内容(リアクティブ変数)が保持される -->
  <!-- 動的コンポーネントはv-bind:isを使用してコンポーネントを渡す -->
  <KeepAlive>
    <component v-bind:is="currentComp" />
  </KeepAlive>
  <button @click="switchComp">切り替え</button>
</template>

<style>
section {
  border: blue 1px solid;
  margin: 10px;
}
</style>