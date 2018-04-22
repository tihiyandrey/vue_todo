<template>
  <div>
    <header>
      <h1>{{ msg }}</h1>
      <input type="text" class="add" placeholder="What needs to be done?" autofocus="autofocus" v-model="newTodo" @keyup.enter="addTodo">
    </header>
    <main>
      <section>
        <ul class="todo-list">
          <li class="todo" v-for="todo in todos" :class="{completed: todo.completed}">
            <div class="view">
              <input type="checkbox" v-model="todo.completed" class="toggle">
              <label>{{ todo.name }}</label>
            </div>
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'todos',
      todos: [{
        name: 'test 123',
        completed: false
      }],
      newTodo: ''
    }
  },
  methods: {
    addTodo () {
      this.todos.push({
        completed: false,
        name: this.newTodo
      })
      this.newTodo = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  text-align: center;
}
h1{
    font-size: 100px;
    font-weight: 100;
    text-align: center;
    color: rgba(175, 47, 47, 0.15);
    margin: 0;
    padding: 0;
}
.add {
  position: relative;
  width: 40%;
  min-width: 300px;
  font-size: 24px;
  border: none;
  box-sizing: border-box;
  padding: 16px 16px 16px 60px;
  background: #fff;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
input.add::-webkit-input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

input.add::-moz-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

input.add::input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}
main {
  width: 40%;
  margin: auto;
  background: #fff;
  position: relative;
  border-top: 1px solid #e6e6e6;
}
.todo-list {
  margin: 0;
  padding: 0;
  list-style: none;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
.todo-list li {
  position: relative;
  font-size: 24px;
  border-bottom: 1px solid #ededed;
}
.todo-list li label {
  white-space: pre-line;
  word-break: break-all;
  padding: 15px 60px 15px 15px;
  margin-left: 45px;
  display: block;
  line-height: 1.2;
  transition: color 0.4s;
}
.todo-list li.completed label {
  color: #d9d9d9;
  text-decoration: line-through;
}
.todo-list li .toggle {
  text-align: center;
  width: 40px;
  height: auto;
  position: absolute;
  top: 8px;
  bottom: 0;
  margin: auto 0;
  border: none;
  -webkit-appearance: none;
  appearance: none;
}
.todo-list li .toggle:after {
  content: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="-10 -18 100 135"><circle cx="50" cy="50" r="50" fill="none" stroke="#ededed" stroke-width="3"/></svg>');
}
.todo-list li .toggle:checked:after {
  content: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="-10 -18 100 135"><circle cx="50" cy="50" r="50" fill="none" stroke="#bddad5" stroke-width="3"/><path fill="#5dc2af" d="M72 25L42 71 27 56l-4 4 20 20 34-52z"/></svg>');
}
input[type="checkbox"] {
    outline: none;
}
</style>