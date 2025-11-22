<!-- ChildComponent2.vue -->
<template>
  <div>
    <p>{{ sharedMessage }}</p>
  </div>
</template>

<script setup lang="ts">
import { inject, Ref } from 'vue';

const injected = inject<Ref<string>>('sharedMessage');
const sharedMessage = injected ? injected.value : '';
</script>

<style scoped>
p {
  font-size: 1.5rem;
}
</style>
