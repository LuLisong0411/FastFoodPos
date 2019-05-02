<template>
  <div id="app">
    <i class="icon iconfont icon-shezhi"></i>
    <i class="icon iconfont icon-jine"></i>
    <i class="icon iconfont icon-ziyuan"></i>
    <i class="icon iconfont icon-wode"></i>
    <i class="icon iconfont icon-dianpu-xuanzhong"></i>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
};
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
