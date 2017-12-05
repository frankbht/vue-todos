<template>
  <div>
    <input type="text" v-model="term" @input="onInputChange"/>
    <button @click="addNewTodo">Add Todo</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      term: ''
    }
  },
  methods: {
    onInputChange(e) {
      this.term = event.target.value;
    },
    addNewTodo() {
      this.$emit("addTodo", this.term);
      this.term = '';
    }
  }
}
</script>

