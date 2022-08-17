<script setup>
import { computed } from 'vue'

const props = defineProps({
  modelValue: String,
  type: {
    type: String,
    default: 'text',
  },
  hasError: {
    type: Boolean,
    default: false,
  },
})
const emit = defineEmits(['update:modelValue'])

const model = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
})
</script>

<template>
  <div>
    <input
      :class="{ error: hasError }"
      :type="type"
      v-model="model"
      placeholder="Add Todo Here"
    />
  </div>
</template>

<style scoped>
input {
  width: 250px;
  height: 40px;
  margin-right: 10px;
}

input.error {
  border: 1.5px solid red;
}
</style>
