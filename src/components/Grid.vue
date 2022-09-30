<script setup>
import Word from "./Word.vue";
import {onMounted, ref} from "vue";

const words = {
  FID: 'First input delay',
  TLA: 'Three letter acronym',
  WTF: 'What the 🤬',
  CLS: 'Cumulative layout shift',
  LCP: 'Largest contentful paint',
  CWV: 'Core web vitals',
  CSR: 'Client side rendered',
  SSR: 'Server side rendered',
  SPA: 'Single page app',
  TBT: 'Total blocking time',
  RUM: 'Real user monitoring',
  PSI: 'Page speed index',
  GSC: 'Google search console',
  SEO: 'Search engine optimisation',
  PNX: 'Previous Next',
  RSI: 'Repetitive strain injury',
  TTI: 'Time to interactive',
  FCP: 'First contentful paint',
  CSS: 'Cascading style sheets',
  CSP: 'Content security policy',
  CI: 'Continuous integration',
  CD: 'Continuous delivery',
  PAAS: 'Product as a service',
  TTFB: 'Time to first byte',
  GTM: 'Google tag manager',
}
const highlighted = ref([]);

const sorted = ref([]);

const last = ref('click an item');

onMounted(() => {
  sorted.value = shuffle(Object.keys(words));
})

const shuffle = array => array.sort(() => Math.random() - 0.5);
const toggleWord = (word) => {
  last.value = words[word];
  if (highlighted.value.includes(word)) {
    highlighted.value = highlighted.value.filter(item => item !== word);
    return;
  }
  highlighted.value.push(word);
}

</script>
<template>
  <div class="grid">
    <div v-for="word in sorted" :key="word"><Word :word="word" :checked="highlighted.includes(word)" @toggleword="toggleWord"/></div>
  </div>
  <div class="last">{{ last }}</div>
</template>
<style scoped>
.grid {
  display: grid;
  grid-template-rows: repeat(5, 1fr);
  grid-template-columns: repeat(5, 1fr);
  gap: .25rem;
  @media(min-width: 600px) {
    gap: 1rem;
  }
}
.last {
  margin-top: 3rem;
  font-size: 2rem;
  @media(min-width: 600px) {
    font-size: 3rem;
  }
}
</style>