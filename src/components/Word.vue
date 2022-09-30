<script setup>
const props = defineProps({
  word: {
    type: String,
    default: '',
  },
  checked: {
    type: Boolean,
    default: false,
  }
})
const emits = defineEmits(['toggleword'])
</script>
<template>
  <div class="word">
    <button @click="() => emits('toggleword', word)" :class="`${checked ? 'word--checked' : ''}`">{{ word }}</button>
  </div>
</template>
<style scoped>
  :root {
    --pnx-light-blue: #c8f1ff;
    --pnx-dark-blue: #161b59;
  }
  button {
    width: 100%;
    padding: 1rem;
    font-weight: bold;
    @media (min-width: 600px) {
      padding: 2rem;
      font-size: 3rem;
    }
  }
  button.word--checked {
    background-color: var(--pnx-light-blue);
    color: var(--pnx-dark-blue);
  }
</style>