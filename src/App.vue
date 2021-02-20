<template>
  <div id="app">
    <div id="nav">
      <Logout />> <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>|
      <router-link to="/login">login</router-link>|
      <router-link to="/register">register</router-link>|
      <router-link to="/secret">secret</router-link>
    </div>
    <router-view />
  </div>
</template>
<script>
import Logout from "./components/Top-Header.vue";
export default {
  name: "App",
  components: { Logout },
};
</script>
<style lang="scss">
#app {
  font-family: "sans-serif";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
