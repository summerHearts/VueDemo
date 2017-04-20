<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 v-text = "title"></h1>
    <h1 v-html= "subtitle"></h1>
     <ol>
      <li v-for="todo in todos">
         {{ todo.text }}
      </li>
     </ol>
    <p v-if>现在你看到我了</p>
    <p>{{ message }}</p>
    <input v-model="message">
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
              { text: '学习 JavaScript' },
              { text: '学习 Vue' },
              { text: 'Vue 开发教程' }
           ]
      }
    },
      methods:  {
        toggleFinish:function (item){
          console.log(item)
        },
        reverseMessage: function () {
            this.message = this.message.split('').reverse().join('')
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
