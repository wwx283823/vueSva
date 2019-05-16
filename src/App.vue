<template>
  <div id="app" style="margin-top: 0px;text-align: left" >
    <!--<img src="./assets/logo.png">
    <h1>{{msg}}</h1>-->
    <!--<wrapper></wrapper>-->
    <!--<firstcomponent></firstcomponent>-->
    <!--<hello></hello>-->
    <!--<router-view v-if="isRouterAlive"></router-view>-->
    <wrapper></wrapper>
    <!--<menu-id></menu-id>-->
    <!-- 路由出口 -->
    <!-- 路由匹配到的组件将渲染在这里 -->
  </div>
</template>
<style scoped>
  @import '../static/css/app.css';
</style>
<script>
  import firstcomponent from './components/FirstComponent.vue'
  import hello from './components/HelloWorld.vue'
  import wrapper from './components/test.vue'
  import menuId from './components/Menu.vue'
  export default {
    name: 'app',
//    provide(){
//      return this.reload
//    },
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    components: {firstcomponent,hello,menuId,wrapper},
//    methods:{
//        reload(){
//          this.isRouterAlive = false;
//          this.$nextTick(function () {
//            this.isRouterAlive = true;
//          })
//        }
//    }
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
