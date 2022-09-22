<template>
  <div class="title">
    <router-link to="/mqm">
      <div class="item">mqm</div>
    </router-link>
    <router-link to="/">
      <div class="item">qiu</div>
    </router-link>
    <router-link to="/drag">
      <div class="item">dianci</div>
    </router-link>
    <router-link to="/animation">
      <div class="item">animation</div>
    </router-link>
  </div>

  <router-view/>
</template>

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
}

.title {
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #2c3e50;
  /* position: fixed; */
}
.title a {
  text-decoration: none;
}
.title a.router-link-exact-active {
  color: #42b983;
}
.title .item {
  padding: 0 30px;
}
</style>
