<template>
  <v-container>
    <v-card>
      <v-card-text class="text-h5"> Счётчик: {{ counter }} </v-card-text>
      <v-card-actions>
        <v-btn color="orange" @click="incrementCounter">+</v-btn>
        <v-btn color="orange" @click="decrementCounter">-</v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'SimpleCounter',
  data() {
    return {
      counter: 0,
    }
  },
  mounted() {
    this.counter = localStorage.getItem('counter') || 0
  },
  methods: {
    incrementCounter() {
      this.counter++
      this.saveCounter()
    },
    decrementCounter() {
      this.counter--
      this.saveCounter()
    },
    saveCounter() {
      localStorage.setItem('counter', this.counter)
    },
  },
}
</script>

<style></style>
