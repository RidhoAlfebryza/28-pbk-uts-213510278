<template>
  <div id="nav" class="navbar">
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li><router-link to="/about">About</router-link></li>
      <li><router-link to="/todo">Todo List</router-link></li>
    </ul>
  </div>
  <router-view />
</template>

<style>
#nav {
  padding: 30px;
  align-items: center;
}

#nav a {
  font-weight: bold;
  color: white;
}

#nav a.router-link-exact-active {
  color: greenyellow;
}

.navbar li{
  display: inline-block;
}

.navbar ul{
  overflow: hidden;
}


a {
  display: block;
  padding: 8px;

}
</style>