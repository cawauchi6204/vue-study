<script setup lang="ts">
interface Props {
  name: string
}

defineProps<Props>()
</script>

<template>
  <section class="box">
    <h1>{{ name }}さんの状況</h1>
    <!-- reactでいうchildrenのようなもの -->
    <slot>
      <p>{{ name }} さんは連絡が付きません</p>
    </slot>
    <slot name="detail">
      <p>特にありません</p>
    </slot>
  </section>
</template>

<style scoped>
.box {
  border: green 1px dashed;
  margin: 10px;
}
</style>