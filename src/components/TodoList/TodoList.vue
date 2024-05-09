<template>
  <v-container>
    <v-form class="mb-4" @submit.prevent="createNewTodo">
      <v-text-field v-model="newTodo" label="Todo text" />
      <v-btn color="orange" type="submit">Add item</v-btn>
    </v-form>
    <template v-if="list.length">
      <TodoListItem
        v-for="todo in list"
        :item="todo"
        :key="todo.id"
        class="mb-4"
        @deleteItem="deleteTodo"
        @updateItem="updateTodo"
      />
    </template>
    <div v-else>List is empty</div>
  </v-container>
</template>

<script>
import TodoListItem from './TodoListItem.vue'
export default {
  components: {
    TodoListItem,
  },
  data() {
    return {
      list: [
        {
          id: 1,
          text: 'Todo 1',
          checked: false,
        },
        {
          id: 2,
          text: 'Todo 2',
          checked: false,
        },
        {
          id: 3,
          text: 'Todo 3',
          checked: false,
        },
      ],
      newTodo: '',
    }
  },
  methods: {
    deleteTodo(id) {
      this.list = this.list.filter((todo) => todo.id !== id)
    },
    createNewTodo() {
      if (!this.newTodo) return

      this.list.unshift({
        id: (Math.random() * 1e8).toString(16),
        text: this.newTodo,
        checked: false,
      })
      this.newTodo = ''
    },
    updateTodo(newTodo) {
      const index = this.list.find((item) => item.id === newTodo.id)
      this.list[index] = { ...newTodo }
    },
  },
}
</script>

<style></style>
