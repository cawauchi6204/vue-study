<script setup lang="ts">
import { computed, ref } from "vue";
import OneMember from "./components/OneMember.vue"

const memberListInit = new Map<number, Member>();
memberListInit.set(33356, { id: 33356, name: "山田太郎", email: "bow@example.com", points: 35, note: "初回入会特典あり" });
memberListInit.set(47783, { id: 47783, name: "鈴木花子", email: "mue@example.com", points: 53 })
const memberList = ref(memberListInit)

const totalPoints = computed(
  () => {
    let total = 0;
    for (const member of memberList.value.values()) {
      total += member.points;
    }
    return total
  }
)

interface Member {
  id: number
  name: string
  email: string
  points: number
  note?: string
}
</script>

<template>
  <h1>会員リスト</h1>
  <p>全会員の保有ポイントの合計: {{ totalPoints }}</p>
  <OneMember v-for="[id, member] in memberList" :key="id" :id="id" :name="member.name" :email="member.email"
    :note="member.note" v-model:points="member.points" />
</template>

<style>
section {
  border: blue 1px solid;
  margin: 10px;
}
</style>