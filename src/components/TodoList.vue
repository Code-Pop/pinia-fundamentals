<script setup>
import { useTodoListStore } from '@/stores/useTodoListStore'
import { storeToRefs } from 'pinia'

const store = useTodoListStore()

// storeToRefs lets todoList keep reactivity:
const { todoList } = storeToRefs(store)

// destructuring action method doesn't require using storeToRefs:
const { toggleCompleted, deleteTodo } = store

</script>

<template>
  <div v-for="todo in todoList" :key="todo.id" class="item">
    <div class="content">
      <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
      <div>
        <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
        <span @click="deleteTodo(todo.id)" class="x">&#10060;</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>