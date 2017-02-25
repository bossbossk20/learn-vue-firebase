
<template>
  <div id="app">
    <div id='app'>
    Name <input type="text" v-model="name"> <br>
    Number <input type="text" v-model="number"> <br>
    IMG <input type="text" v-model="img"> <br>
    <button @click="addTodo()">Add</button>
    <div v-for="todo in todos" class="phonebook">
      {{ todo.name }} {{ todo.number}}   <img :src="todo.img" alt="">
    </div>
  </div>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
import firebase from 'firebase'
let firebaseApp = firebase.initializeApp({
  apiKey: 'AIzaSyACYRwkmpkljY8cZAXLKdtlTy2XfvZAVx4',
  authDomain: 'fire-49ce0.firebaseapp.com',
  databaseURL: 'https://fire-49ce0.firebaseio.com',
  storageBucket: 'fire-49ce0.appspot.com',
  messagingSenderId: '1092622780937'
})
let db = firebaseApp.database()

export default {
  name: 'app',
  data () {
    return {
      name: '',
      number: '',
      img: ''
    }
  },
  firebase: {
    todos: db.ref('todos')
  },
  methods: {
    addTodo () {
      this.$firebaseRefs.todos.push({
        name: this.name,
        number: this.number,
        img: this.img
      })
    }
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
</style>
