<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'E09CompositionApi',
});
</script>

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

// props 정의
const props = defineProps<{
  title?: string;
}>();

const title = computed(() => props.title ?? 'User Information');

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
  console.log('[E09] greetCount changed', oldVal, '=>', newVal);
});

onBeforeMount(() => console.log('[E09] beforeMount hook'));
onMounted(() => console.log('[E09] mounted hook'));
onBeforeUpdate(() => console.log('[E09] beforeUpdate hook'));
onUpdated(() => console.log('[E09] updated hook'));
onBeforeUnmount(() => console.log('[E09] beforeUnmount hook'));
onUnmounted(() => console.log('[E09] unmounted hook'));
</script>

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
