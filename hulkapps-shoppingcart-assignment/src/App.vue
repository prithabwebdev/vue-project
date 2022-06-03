<template>
  <div>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Cart/>
    <Header/>
    <div class="container">
      
        <Description/>
        <Home/>
      
    </div>  
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Home from './components/Home.vue'
import Cart from './components/Cart.vue'
import Description from './components/Description.vue'

export default {
  name: 'App',
  components: {
    Header,
    Home,
    Cart,
    Description
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
</style>
