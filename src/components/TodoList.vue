<script setup>
import { useTodoListStore } from '@/stores/useTodoListStore'
import { storeToRefs } from 'pinia'

const store = useTodoListStore();

// storeToRefs lets todoList keep reactivity:
const { todoList } = storeToRefs(store)

</script>

<template>
  <div v-for="todo in todoList" :key="todo.id">
    <div>{{ todo.item }}</div>
  </div>
</template>

<style scoped>
</style>