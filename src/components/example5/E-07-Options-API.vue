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

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'E07OptionsApi',

  data() {
    return {
      title: 'User Information',
      firstName: 'Kyungsu',
      lastName: 'Lee',
      greetCount: 0,
      message: '',
    };
  },

  computed: {
    fullName(): string {
      return `${this.firstName} ${this.lastName}`;
    },
  },

  methods: {
    greet() {
      this.greetCount++;
      this.message = `Hello, ${this.fullName}!`;
    },
    resetGreetCount() {
      this.greetCount = 0;
    },
  },

  watch: {
    greetCount(newVal: number, oldVal: number) {
      console.log('greetCount changed', oldVal, '=>', newVal);
    },
  },

  beforeMount() {
    console.log('beforeMount hook');
  },

  mounted() {
    console.log('mounted hook');
  },

  beforeUpdate() {
    console.log('beforeUpdate hook');
  },

  updated() {
    console.log('updated hook');
  },

  beforeUnmount() {
    console.log('beforeUnmount hook');
  },

  unmounted() {
    console.log('unmounted hook');
  },
});
</script>
