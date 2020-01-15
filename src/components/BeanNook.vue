<template>
  <div class="nook">
    <div class="nook-title">
      <h4 class="title is-4 has-text-primary">
        {{ nook.name }}
      </h4>
    </div>
    <div class="nook-city is-inline-flex">
      <div class="has-text-weight-bold has-text-primary">{{ nook.city }}, {{ nook.state }}</div>
      <a
        class="icon has-text-primary"
        :href="`https://www.google.com/maps/place/${nook.street},+${nook.city},+${nook.state}+${nook.zip_code}/`">
        <font-awesome-icon class="nav-icon" icon="directions" />
      </a>

    </div>
    <div class="">
      <div class="nook-summary">
        {{ nook.commentary }} - <span class="has-text-primary has-text-weight-bold">libby</span>
      </div>
      <figure class="image">
        <img alt="Pick" :src="nook.images[0].url" v-if="nook.images[0]">
        <bean-cursor v-else/>
      </figure>
    </div>
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import {
  faDirections
} from '@fortawesome/free-solid-svg-icons'

library.add(
  faDirections
)

export default {
  props: ['nook']
}
</script>

<style lang="sass" scoped>
  @import "@/sass/custom.sass"
  @import "~bulma/bulma"
  +until(550px)
    .img
      display: flex
      justify-content: center
  .nook
    margin-bottom: 2rem
  .nook-title
    display: flex
    flex-direction: column
    align-items: flex-start
    margin-bottom: .25rem
  .nook-city
    margin-bottom: .25rem
  .nook-summary
    padding-bottom: 1rem
</style>
