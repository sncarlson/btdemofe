<template>
  <!--

  -->
  <Header />
  <router-view/>
</template>

<script>

import Header from './components/layout/Header';

export default {
  name:"app",
  components: {
    Header
  }
}
</script>


<style>
#app {
  text-align: center;
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
