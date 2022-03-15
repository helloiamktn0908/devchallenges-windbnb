<template>
  <!-- <Header v-bind:msg="1234" /> -->
  <Drawer />
</template>

<script lang="ts">
import 'normalize.css';
import { defineComponent } from 'vue';
import Header from './components/Header.vue';
import Drawer from './components/Drawer.vue';

export default defineComponent({
  components: {
    Header,
    Drawer,
  },
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@200;300;400;500;600;700;800&display=swap');
#app {
  font-family: 'Mulish', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333333;
}
</style>
