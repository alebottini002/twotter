<template>
  
  <div id="app">
    <UserProfile/>
    <TwootItem/>
  </div>

</template>

<script>

import UserProfile from "./components/UserProfile";
import TwootItem from "./components/TwootItem";

export default {

  name: 'App',
  components: {UserProfile, TwootItem}

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  text-align: center;
  
}
</style>
