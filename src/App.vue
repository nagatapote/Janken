<template>
  <div id="app">
    <h1>じゃんけんゲーム</h1>
    <div id="nav">
      <router-link to="/">ゲーム</router-link> |
      <router-link to="/About">このゲームについて</router-link>
    </div>
    <router-view scores="scores" />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
