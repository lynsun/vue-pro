<template>
  <div id="app">
    hello <el-button>world</el-button>
  </div>
</template>

<script>
import Vue from 'vue';
import elButton from 'element-ui/lib/button';

Vue.component(elButton.name, elButton);

export default {
  name: 'app',
  components: {
    elButton,
  },
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
