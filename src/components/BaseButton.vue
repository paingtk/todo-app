<script setup>
defineProps({
  name: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div>
    <button>{{ name }}</button>
  </div>
</template>

<style scoped>
button {
  width: 80px;
  height: 40px;
}
</style>
