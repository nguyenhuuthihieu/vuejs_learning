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
    <br/>
    <component2 v-bind:postTitle="message"/>
    <br/>
    <component/>
  </div>
</template>

<script>
  import component2 from './component2.vue';
  import component from './component.vue';
  export default {
    name: 'HelloWorld',
    components: {component2, component},
    props: {
      postTilte:String,
      // Basic type check (`null` matches any type)
      propA: Number,
      // Multiple possible types
      propB: [String, Number],
      // Required string
      propC: {
        type: String,
        required: true
      },
      // Number with a default value
      propD: {
        type: Number,
        default: 100
      },
      // Object with a default value
      propE: {
        type: Object,
        // Object or array defaults must be returned from
        // a factory function
        default: function () {
          return { message: 'hello' }
        }
      },
      // Custom validator function
      propF: {
        validator: function (value) {
          // The value must match one of these strings
          return ['success', 'warning', 'danger'].indexOf(value) !== -1
        }
      }
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
