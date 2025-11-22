<!-- ChildComponent.vue -->
<template>
  <div>
    <p>{{ message }}</p>
    <button @click="sendEvent">Send Event</button>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  message: string;
}>();

const emit = defineEmits<{
  (e: 'custom-event', payload: string): void;
}>();

const sendEvent = () => {
  emit('custom-event', 'Hello from child');
};
</script>
