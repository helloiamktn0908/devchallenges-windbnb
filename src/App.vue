<template>
  <Header />
  <Stays />
</template>

<script lang="ts">
import 'normalize.css';
import { defineComponent } from 'vue';
import Header from './components/Header.vue';
import Stays from './components/Stays.vue';

export default defineComponent({
  components: {
    Header,
    Stays,
  },
  data() {
    return {
      isHeaderOpen: false,
    };
  },
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@200;300;400;500;600;700;800&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200;300;400;500;600;700;800;900&display=swap');
#app {
  font-family: 'Mulish', 'Montserrat', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333333;
}
</style>
