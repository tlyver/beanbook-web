<template>
  <div>
    <div class="nook">
      <h4 class="title is-4 has-text-primary">
        {{ format(new Date(nook.featured_date), 'MMMM') }}
        {{ `'${format(new Date(nook.featured_date), 'yy')}` }}
      </h4>
    </div>
    <div class="">
      <div class="nook-summary">
        <span class="has-text-weight-bold has-text-primary">{{ nook.name}}</span>
        {{ `- ${nook.commentary}` }}
      </div>
      <figure class="image">
        <img alt="Pick" :src="nook.images[0].url" v-if="nook.images[0]">
        <bean-cursor v-else/>
      </figure>
    </div>
  </div>
</template>

<script>
import { format } from 'date-fns'

export default {
  props: ['nook'],
  data () {
    return {
      format
    }
  }
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
    display: flex
    flex-direction: column
    align-items: flex-start
    margin-bottom: 1rem
  .nook-summary
    padding-bottom: 1rem
</style>
