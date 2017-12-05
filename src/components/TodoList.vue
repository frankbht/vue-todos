<template>
  <div>
    <ul>
      <li 
        v-for="(todo, index) in dataToShow" 
        :key="index"
        >
        <span style="vertical-align: middle" :class="{ checked: todo.done }">{{index}}. {{ todo.title | capitalInit }}</span>
        <span>
          <button @click="checkTodo(todo.title)"><img src='https:icon.now.sh/check' alt='check icon' /></button>
          <button @click="deleteTodo(todo.title)"><img src='https:icon.now.sh/delete' alt='delete icon' /></button>
        </span>
      </li>
    </ul>
    <!-- <p>{{ group }}</p> -->
  </div>
</template>
<script>
export default {
  props: ['todos', 'group'],
  methods: {
    deleteTodo(title) {
      this.$emit('deleteTodo', title);
    },
    checkTodo(title) {
      this.$emit('checkTodo', title);
    },
    editTodo() {

    }
  },
  computed: {
    dataToShow() {
      if(this.group==="all") {
        return this.todos
      } else if(this.group==="done") {
        return this.todos.filter((element) => element.done===true).map((element) => {
            return {
              title: element.title,
              done: false
            }
        })
      } else {
        return this.todos.filter((element) => element.done===false)
      }
    }
  },
  filters: {
    capitalInit(value) {
      return value.charAt(0).toUpperCase() + value.slice(1);
    }
  }
}
</script>
