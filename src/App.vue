<template>
  <div id="app">
    <h1>My Todos</h1>
    <input-bar :todos="todos" @addTodo="addNewTodo"></input-bar>
    <tag-group :group="group" @groupChanged="changeGroup"></tag-group>
    <todo-list 
      :todos="todos"
      :group="group"
      @deleteTodo="deleteTodo"
      @checkTodo="checkTodo">
    </todo-list>
  </div>
</template>

<script>
import InputBar from './components/InputBar.vue';
import TodoList from './components/TodoList.vue';
import TagGroup from './components/TagGroup.vue';

export default {
  name: 'app',
  data () {
    return {
      group: "all",
      todos: [
        {
          title: 'eat',
          done: false
        },
        {
          title: 'code',
          done: false
        },
        {
          title: 'sleep',
          done: false
        }
      ]
    }
  },
  methods: {
    addNewTodo(event) {
      console.log(event)
      this.todos.push({
        title: event,
        done: false
      })
    },
    deleteTodo(title) {
      const index = this.todos.findIndex((element) => element.title === title);
      if(index != -1) {
        this.todos.splice(index, 1);
      }
    },
    checkTodo(title) {
      const index = this.todos.findIndex((element) => element.title === title);
      if(index != -1) {
        this.todos[index].done = !this.todos[index].done;
      }
    },
    changeGroup(group) {
      this.group = group;
    }
  },
  components: {
    InputBar,
    TodoList,
    TagGroup
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
  display: flex;
  flex-direction: row;
}

li span {
  flex: 0 50%;
  margin-left: 300px;
  text-align: left;
}

a {
  color: #42b983;
}

.checked {
  text-decoration:line-through;
}

.tag-group {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.tag-item {
  text-align: center;
}

.active {
  border-bottom: 1px solid #42b983;
}

.tag-item:hover {
  color:#42b983;
  cursor: default;
}
</style>
