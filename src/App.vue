<template>
  <div>
    <Navbar />
    <router-view class="mainContent" />
    <FooterCompVue />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import FooterCompVue from "./components/FooterComp.vue";

export default {
  components: {
    Navbar,
    FooterCompVue,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  width: 100%;
}
body {
  width: 100%;
  background: #f2f2f2;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 900px;
  width: 90%;
  margin: 0 auto;
  color: #2c3e50;
}
.mainContent {
  min-height: calc(100vh - 25rem);
}
</style>
