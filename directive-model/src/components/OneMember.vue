<script setup lang="ts">
import { computed, ref } from 'vue';


interface Props {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}

const props = defineProps<Props>()

// 一度リアクティブ変数にして変更している
// 個々のpropsはreadonlyなので、直接変更できない
const localPoints = ref(props.points)
const localNote = computed(
  () => {
    if (localNote == undefined)
      return "--"
    return props.note
  }
)
const pointUp = () => {
  localPoints.value++
}
</script>

<template>
  <section class="box">
    <h4>{{ name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ localPoints }}</dd>
      <dt>備考</dt>
      <dd>{{ localNote }}</dd>
    </dl>
    <button @click="pointUp">ポイント加算</button>
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>