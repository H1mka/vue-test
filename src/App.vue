<template>
  <v-app>
    <v-main>
      <SimpleCounter />
      <TodoList />
    </v-main>
  </v-app>
</template>

<script>
import SimpleCounter from './components/Counter/SimpleCounter.vue'
import TodoList from './components/TodoList/TodoList.vue'
export default {
  name: 'App',
  components: {
    SimpleCounter,
    TodoList,
  },

  data: () => ({
    //
  }),
}
</script>
