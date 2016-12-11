<template>
  <nav>
    <a href="javascript:;" class="button sites-button" v-on:click="sitesMenuOpen = !sitesMenuOpen; userMenuOpen = false">{{sitename}} sites</a>
    <ul v-show="sitesMenuOpen" class="menu sites-menu">
      <li><a href="http://gizmodo.com">Gizmodo</a></li>
      <li><a href="http://lifehacker.com">Lifehacker</a></li>
      <li><a href="http://jezebel.com">Jezebel</a></li>
      <li><a href="http://kotaku.com">Kotaku</a></li>
      <li><a href="http://jalopnik.com">Jalopnik</a></li>
      <li><a href="http://deadspin.com">Deadspin</a></li>
    </ul>
    <a href="javascript:;" class="button user-button" v-on:click="userMenuOpen = !userMenuOpen; sitesMenuOpen = false">user</a>
    <ul v-show="userMenuOpen" class="menu user-menu">
      <li>Welcome {{ username }}</li>
      <li><a href="javascript:;">Account settings</a></li>
      <li><a href="javascript:;">Write a post</a></li>
      <li><a href="javascript:;">Superuser settings</a></li>
      <li><a href="javascript:;">Logout</a></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'navbar',
  data () {
    return {
      userMenuOpen: false,
      sitesMenuOpen: false,
      sitename: 'kinja.com',
      username: 'serif'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid lightgrey;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.menu {
  position: absolute;
  top: 15px;
  background-color: lightgrey;
  border: 1px solid grey;
}
.sites-menu {
  left: 0;
}
.user-menu {
  right: 0;
}

.button {
  display: inline-block;
  padding: 0.3em;
  /*border: 1px solid grey;*/
  /*background-color: lightgrey;*/
}
</style>
