<template>
  <div>
    {{msg}}
    <div>
      <ol>
        <li v-for="todo in todos" :key="todo.id">
          {{ todo.text }}
        </li>
      </ol>
    </div>
    <div>
      <p>{{ message }}</p>
      <input v-model="message">
    </div>
    <div>
      <p>{{ message }}</p>
      <button v-on:click="reverseMessage">Reverse Message</button>
    </div>
    <component2 v-bind:postTitle="message"/>
  </div>
</template>

<script>
  import component2 from './component2.vue';
  export default {
    name: 'HelloWorld',
    components: {component2},
    props: {
      postTilte:String,
    },
      data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        todos: [
          { text: 'Học JavaScript' },
          { text: 'Học Vue' },
          { text: 'Xây dựng cái gì đó hay ho' }
        ],
        message: 'Hãy sửa thông điệp này',
      }
    },
    methods: {
      reverseMessage: function () {
        this.message = this.message.split(' ').reverse().join(' ')
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
