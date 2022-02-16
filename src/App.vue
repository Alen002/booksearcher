<template><the-header /><home /><the-footer /></template>

<script>
import Home from '@/views/Home.vue';
import TheHeader from '@/components/TheHeader.vue';
import TheFooter from '@/components/TheFooter.vue';
export default {
  name: 'App',
  components: { TheHeader, Home, TheFooter },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}
html {
  font-family: 'Roboto', sans-serif;
}
body {
  margin: 0;
  background-color: lightblue;
}
</style>
