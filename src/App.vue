<template>
  <div id="app">
    <hello></hello>
    <v-button @click.native="onClick">button</v-button>
    <v-tabs :headers="apps">
      <v-tab v-for="app in apps" :header="app">{{app}}</v-tab>
    </v-tabs>
  </div>
</template>

<script>
import Vue from 'vue';
import atui from 'atui';
import 'atui/dist/greater-blue.css';

import Hello from './components/Hello';

// Vue.component(elButton.name, elButton);
Vue.use(atui)

export default {
  name: 'app',
  components: {
    Hello,
    vTabs,
    vTab,
    vButton,
    // elButton,
  },
  data() {
    return {
      apps: [
        'tab1', 'tab2',
      ],
    };
  },
  methods: {
    onClick() {
      console.log(111);
      this.apps.splice(0, 1);
    },
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
