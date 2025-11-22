<template>
  <div>
    <h2>{{ title }}</h2>
    <p>Full Name: {{ fullName }}</p>
    <input v-model="firstName" placeholder="First Name" />
    <input v-model="lastName" placeholder="Last Name" />
    <button @click="greet">Greet</button>
    <button @click="resetGreetCount">Reset</button>
    <p>Greeting Count: {{ greetCount }}</p>
    <p>{{ message }}</p>
  </div>
</template>

<script setup lang="ts">
import {
  ref,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from 'vue';

const title = ref('User Information');
const firstName = ref('Kyungsu');
const lastName = ref('Lee');
const greetCount = ref(0);
const message = ref('');

const fullName = computed(() => `${firstName.value} ${lastName.value}`);

const greet = () => {
  greetCount.value++;
  message.value = `Hello, ${fullName.value}!`;
};

const resetGreetCount = () => {
  greetCount.value = 0;
};

watch(greetCount, (newVal, oldVal) => {
  console.log('greetCount changed', oldVal, '=>', newVal);
});

onBeforeMount(() => console.log('beforeMount hook'));
onMounted(() => console.log('mounted hook'));
onBeforeUpdate(() => console.log('beforeUpdate hook'));
onUpdated(() => console.log('updated hook'));
onBeforeUnmount(() => console.log('beforeUnmount hook'));
onUnmounted(() => console.log('unmounted hook'));
</script>
