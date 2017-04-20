<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 v-text = "title"></h1>
    <h1 v-html= "subtitle"></h1>
     <ul>
      <li v-for="todo in todos" v-bind:class="{finished :todo.isFinished }" v-on:click="toggleFinish(todo)" >
         {{ todo.text }}
      </li>
     </ul>
    <p v-if>现在你看到我了</p>
    <p>{{ message }}</p>
    <input v-model="message" v-on:keyup.enter= "addNewTags">
    <button v-on:click="reverseMessage">逆转消息</button>
  </div>
</template>

<script>
export default {
  data () {
      return {
        message: 'Hello Vue.js!',
        title: 'Welcome to Your Vue.js App',
        subtitle:'<span>?<span>hello vuejs!',
           todos: [

           ]
      }
    },
      methods:  {
        toggleFinish :function (todo){
          todo.isFinished = !todo.isFinished;
          console.log(todo);
        },
        reverseMessage: function () {
            this.message = this.message.split('').reverse().join('')
        },
        addNewTags :function() {
          this.todos.push(
            {
              text: this.message,isFinished: false 
            }
          )
          console.log(this.message)
          this.message= ''
        }
    },
    seen: true
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

.finished{
  text-decoration: underline
}
</style>
