<template>
  <div>
    <header>
      <h1>{{ msg }}</h1>
      <input type="text" placeholder="What needs to be done?" autofocus="autofocus">
    </header>
    <main>
      <section>
        <ul class="todo-list">
          <li class="todo">
            <div class="view">
              <label>first</label>
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
      msg: 'todos'
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
input {
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
input::-webkit-input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

input::-moz-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

input::input-placeholder {
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
</style>