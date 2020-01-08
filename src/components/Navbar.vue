<template>
  <nav class="navbar is-fixed-top is-desktop" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item">
        <router-link :to="{ name: 'about' }">
          <img alt="Vue logo" src="../assets/bean-text.png">
        </router-link>
      </a>
    </div>

    <div class="navbar-menu">
      <div class="navbar-end">
        <a class="navbar-item">
          <router-link :to="{ name: 'about' }">
            <font-awesome-icon class="nav-icon" icon="glasses" />
            <span class="hide-nav-summary">About</span>
          </router-link>
        </a>

        <a class="navbar-item">
          <router-link :to="{ name: 'bookshelf' }">
            <font-awesome-icon class="nav-icon" icon="book" />
            <span class="hide-nav-summary">Bookshelf</span>
          </router-link>
        </a>

        <a class="navbar-item">
          <router-link :to="{ name: 'nooks' }">
            <font-awesome-icon class="nav-icon" icon="store" />
            <span class="hide-nav-summary">Nooks</span>
          </router-link>
        </a>

        <i class="vertically-center">
          <font-awesome-icon icon="grip-lines-vertical" />
        </i>

        <a class="navbar-item has-text-primary" href="https://www.instagram.com/thebeanbookclub/?hl=en">
          <font-awesome-icon :icon="['fab', 'instagram']" />
        </a>
      </div>
    </div>
  </nav>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import {
  faBook,
  faEnvelopeOpenText,
  faGlasses,
  faGripLinesVertical,
  faStore
} from '@fortawesome/free-solid-svg-icons'
import { faInstagram } from '@fortawesome/free-brands-svg-icons'

library.add(
  faBook,
  faEnvelopeOpenText,
  faGlasses,
  faGripLinesVertical,
  faInstagram,
  faStore
)

export default {
}
</script>

<style lang="sass" scoped>
  @import "@/sass/custom.sass"
  @import "~bulma/bulma"
  .nav-icon
    margin-right: .5rem
  .vertically-center
    display: flex
    align-items: center
    color: $danger
  +until(550px)
    .nav-icon
      margin-right: 0rem
    .hide-nav-summary
      display: none
  +until(0px)
    .navbar-menu
      background-color: $background
      box-shadow: 0
      padding: 0
</style>
