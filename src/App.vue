<template>
  <div id="app">
    <header> 
      <router-link to="/listar">Lista imagens</router-link> |
      <router-link to="/">Upload</router-link> |
      <router-link to="/about">About</router-link>
    </header>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

</style>
