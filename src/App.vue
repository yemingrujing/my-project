<template>
  <div id="app">
    <div id="app-in">
      <img src="./assets/logo.png"/>
      <h1>Hello App!</h1>
    </div>
    <ul>
       <li>
         <router-link to="/first">点我跳转到第一页</router-link>
       </li>
       <li>
         <router-link to="/second">点我跳转到第二页</router-link>
       </li>
     </ul>
     <router-view class="view"></router-view>
     <firstcomponent></firstcomponent>
  </div>
</template>

<script>
import firstcomponent from './component/firstcomponent.vue'
export default {
  name: 'app',
  data() {
    return {
      msg: 'Hello Vue!'
    }
  },
  components: {firstcomponent}
}
</script>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

h1,
h2 {
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
