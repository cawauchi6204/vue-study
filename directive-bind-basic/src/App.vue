<script setup lang="ts">
import { ref } from 'vue';

const pMsg = ref("イベント前(ここをクリック!)")
const pBgColorEvent = ref("white")
const onPClickWithEvent = (bgColor: string, event: MouseEvent) => {
  pBgColorEvent.value = bgColor
  pMsg.value = String(event.timeStamp)
}
</script>

<template>
  <p @click="onPClickWithEvent('red', $event)" v-bind:style="{ backgroundColor: pBgColorEvent }">
    {{ pMsg }}
  </p>
</template>