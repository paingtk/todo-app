<script setup>
import { ref, reactive } from 'vue'
import BaseInput from '../components/BaseInput.vue'
import BaseButton from '../components/BaseButton.vue'

const todoInput = ref('')
const hasError = ref(false)
const todoLists = reactive([])

const addNewTodo = () => {
  if (!todoInput.value) {
    hasError.value = true
  } else {
    hasError.value = false
    todoLists.push(todoInput.value)
  }
  todoInput.value = ''
}

const doneTodo = (index) => {
  todoLists.splice(index, 1)
}
</script>

<template>
  <h1>TODO App</h1>
  <div class="input-row">
    <!-- keyup.enter is to submit when user click enter -->
    <BaseInput
      v-model="todoInput"
      @keyup.enter="addNewTodo"
      :hasError="hasError"
    />
    <BaseButton name="Add" @click="addNewTodo" />
  </div>
  <span v-if="hasError">This field is empty!</span>
  <div class="todo-list">
    <div v-for="(list, index) in todoLists" :key="index">
      <div class="list-item">
        <p>{{ list }}</p>
        <BaseButton name="Done" @click="doneTodo(index)" />
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  margin-bottom: 5rem;
}
div.input-row {
  display: flex;
}

span {
  font-size: 12px;
}

div.todo-list {
  margin-top: 5rem;
}

div.list-item {
  display: flex;
  justify-content: space-between;
  margin: 3rem 0;
}

p {
  font-size: 22px;
  font-weight: 500;
  margin: 0;
}
</style>
