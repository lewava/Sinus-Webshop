<template>
  <div id="app">
    <Login v-if="this.$store.state.user.loggedIn" />
    <router-view />
  </div>
</template>

<script>
import Login from "@/components/Login.vue";

export default {
  components: { Login },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: relative;
}
</style>
