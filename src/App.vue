<template>
  <div id="app">
    <div id="nav">
      <navbar/>
    </div>
    <div id="main">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'

export default {
  components: {
    Navbar
  }
}
</script>

<style lang="sass">
@import "@/sass/custom.sass"
@import "~bulma/bulma"
@import "@/sass/global.sass"

#app
  font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: left
  color: #2c3e50

#nav
  padding: 26px
  a
    font-weight: $weight-bold
    &.router-link-exact-active
      color: $bean-orange

#main
  max-width: 769px
  padding: 1rem
  margin: auto
</style>
