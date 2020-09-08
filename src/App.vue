<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Header</router-link> |
      <router-link to="/animations">Animations</router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
// Base
@import "~normalize.css/normalize";
@import "./styles/base/reset.local";
@import "./styles/base/vars";
@import "./styles/utils/mixins";

// Components
@import "./styles/components/form";
@import "./styles/components/buttons";
@import "./styles/components/links";
@import "./styles/components/flip-card";

html,
body {
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    color: #2c3e50;
    font-weight: bold;
    font-size: 24px;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
