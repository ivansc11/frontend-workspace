<template>
  <div id="app">
    <div id="nav" class="d-flex justify-content-between text-center ">
      <img alt="Arq3D logo" class="m-3" src="./assets/logo.png" />
      <div class="p-3">
        <router-link class="align-middle" to="/">Dashboard</router-link> |
        <router-link to="/profile">Perfil</router-link> |
        <router-link to="/projects">Proyectos</router-link> |
        <router-link to="/chat">Chat</router-link> |
        <router-link to="/notas">Log out</router-link>
      </div>
    </div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
#nav img {
  height: 100px;
}
</style>
