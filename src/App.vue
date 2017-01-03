<template>
  <div id="app">
    <hello></hello>
    <v-button>button</v-button>
  </div>
</template>

<script>
import atui from 'atui';
import 'atui/dist/greater-blue.css';

import Hello from './components/Hello';

const vButton = atui.Button;

export default {
  name: 'app',
  components: {
    Hello,
    vButton,
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
