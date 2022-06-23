<template>
  <div>
    <HeaderComp />
    <SignUpForm />
  </div>
</template>

<script>

import SignUpForm from './components/SignUpForm.vue'
import HeaderComp from './components/Header.vue';

export default {

  name: 'App',
  components: {
    SignUpForm,
    HeaderComp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eee;
}
</style>
