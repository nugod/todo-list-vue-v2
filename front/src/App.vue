<template>
  <div id="app">
    <MyHeader/>
    <b-jumbotron>
      <template v-slot:header>Todo List</template>

      <template v-slot:lead>
        New Features we will have to done for this project
      </template>

      <hr class="my-3">

      <p>
        Easy to use, we created this web app just for you !
      </p>

      <hr class="my-3">

      <router-view :key="$route.fullPath"/>
    
    </b-jumbotron>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'

export default {
  name: 'App',
   components: {
    MyHeader
  } 
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
