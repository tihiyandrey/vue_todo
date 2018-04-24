<template>
  <div>
    <header>
      <h1>{{ msg }}</h1>
      <input type="text" class="add" placeholder="What needs to be done?" autofocus="autofocus" v-model="newTodo" @keyup.enter="addTodo">
    </header>
    <main>
      <section>
        <ul class="todo-list">
          <li class="todo" v-for="todo in filterTodo" :class="{complet: todo.completed}">
            <div class="view">
              <input type="checkbox" v-model="todo.completed" class="toggle">
              <label>{{ todo.name }}</label>
              <button class="delete" @click.prevent="deleteTodo(todo)"></button>
            </div>
          </li>
        </ul>
      </section>
    </main>
    <footer v-show="todos.length > 0">
    	<span class="todo-counter"><strong>{{ counter }}</strong> <span v-if='counter == 1'>item</span><span v-else>items</span> left</span>
      <ul class="filter">
        <li><a href="#" :class="{select: filter == 'all'}" @click.prevent="filter = 'all'">All</a></li>
        <li><a href="#" :class="{select: filter == 'active'}" @click.prevent="filter = 'active'">Active</a></li>
        <li><a href="#" :class="{select: filter == 'completed'}" @click.prevent="filter = 'completed'">Completed</a></li>
      </ul>
    </footer>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'todos',
      todos: [],
      newTodo: '',
      filter: 'all'
    }
  },
  methods: {
    addTodo () {
      this.todos.push({
        completed: false,
        name: this.newTodo
      })
      this.newTodo = ''
    },
    deleteTodo (todo) {
    	this.todos = this.todos.filter(i => i !== todo)
    }
  }, 
  computed: {
  	counter () {
  		return this.todos.filter(todo => !todo.completed).length
  	},
    filterTodo () {
      if (this.filter === 'active') {
         return this.todos.filter(todo => !todo.completed)
      } else if (this.filter === 'completed') {
        return this.todos.filter(todo => todo.completed)
      }
      return this.todos
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
input {outline:none;}
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
.todo-list li.complet label {
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
button, input[type="checkbox"] {
    outline: none;
}
.todo-list li .delete {
	display: none;
	position: absolute;
	top: 0;
	right: 10px;
	bottom: 0;
	width: 40px;
	height: 40px;
	margin: auto 0;
	font-size: 30px;
	color: #cc9a9a;
	margin-bottom: 11px;
	transition: color 0.2s ease-out;
	background: none;
	border: none;
}

.todo-list li .delete:hover {
	color: #af5b5e;
}

.todo-list li .delete:after {
	content: '×';
}

.todo-list li:hover .delete {
	display: block;
}
footer {
	color: #777;
	background-color: #fff;
	padding: 10px 15px;
	height: 40px;
	text-align: center;
	border-top: 1px solid #e6e6e6;
	width: 40%;
    box-sizing: border-box;
    margin: auto;
    position: relative;
}

footer:before {
	content: '';
	position: absolute;
	right: 0;
	bottom: 0;
	left: 0;
	height: 50px;
	overflow: hidden;
	box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2),
	            0 8px 0 -3px #f6f6f6,
	            0 9px 1px -3px rgba(0, 0, 0, 0.2),
	            0 16px 0 -6px #f6f6f6,
	            0 17px 2px -6px rgba(0, 0, 0, 0.2);
}

.todo-counter {
	float: left;
	text-align: left;
}

.todo-counter strong {
	font-weight: 300;
}
.filter {
  margin: 0;
  padding: 0;
  list-style: none;
  position: absolute;
  right: 0;
  left: 0;
}

.filter li {
  display: inline;
}

.filter li a {
  color: inherit;
  margin: 3px;
  padding: 3px 7px;
  text-decoration: none;
  border: 1px solid transparent;
  border-radius: 3px;
}

.filter li a.select,
.filter li a:hover {
  border-color: rgba(175, 47, 47, 0.1);
}

.filter li a.select {
  border-color: rgba(175, 47, 47, 0.2);
}
</style>