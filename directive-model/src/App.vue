<script setup lang="ts">
import { ref } from "vue";
import OneSection from "./components/OneSection.vue";

const taro = ref("田中太郎")
</script>

<template>
  <section>
    <h2>slotの利用</h2>
    <OneSection :name="taro">
      <!-- 名前なしのslotはdefaultになる -->
      <!-- defaultをちゃんと明記しないと表示されない -->
      <template v-slot:default>
        <!-- <template #default> -->
        <!-- この書き方でもおけ -->
        <p>問題発生</p>
      </template>
      <template v-slot:detail>
        <!-- <template #detail> -->
        <!-- この書き方でもおけ -->
        <ul>
          <li>ほげ</li>
        </ul>
      </template>
    </OneSection>
    <OneSection name="ziro" />
  </section>
</template>

<style>
section {
  border: blue 1px solid;
  margin: 10px;
}
</style>