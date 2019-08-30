<template>
  <div id="app">
  <Header></header>
  <div class="main">
    <router-view name="slidebar"></router-view>
    <router-view name="main"></router-view>
    
  </div>
  </div>
</template>


<script>
import Header from './components/Header'
import PostList from './components/PostList'
import Arcicle from './components/Article'
import UserInfo from './components/UserInfo'

export default {
  name: 'App',
  components:{
    Header,PostList,Arcicle,
  }
}
</script>
<style >
 .main {
   width:80%;
   margin:0 auto;
 }
</style>

