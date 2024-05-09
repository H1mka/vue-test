<template>
  <v-card class="d-flex">
    <v-card-text class="d-flex flex-column justify-center" :class="{ completed: checked }">
      <div>{{ item.text }}</div>
    </v-card-text>
    <v-card-actions>
      <v-checkbox v-model="checked" />
      <v-btn icon color="error" @click="deleteItem">
        <v-icon>mdi-delete</v-icon>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
      default: () => ({}),
    },
  },
  data() {
    return {
      checked: this.item.checked || false,
    }
  },
  watch: {
    checked(newValue) {
      this.$emit('updateItem', { ...this.item, checked: newValue })
    },
  },
  methods: {
    deleteItem() {
      this.$emit('deleteItem', this.item.id)
    },
  },
}
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>
