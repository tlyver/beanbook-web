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
        :href="`${nook.map_url}`">
        <font-awesome-icon class="nav-icon" icon="directions" />
      </a>
    </div>
    <div class="">
      <div v-if="commentaryOverflow" class="nook-summary">
        <div v-if="!commentaryExpanded">
          <div>
            <span>{{ nook.commentary.slice(0,500) }}</span><span>...</span> - <span class="has-text-primary has-text-weight-bold">libby</span>
          </div>
          <button
            class="button expand-content is-outlined is-primary is-small"
            type="button"
            name="loadMore"
            @click="toggleDescription"
          >
            More
          </button>
        </div>
        <div v-else class="">
          <div>
            {{ nook.commentary }} - <span class="has-text-primary has-text-weight-bold">libby</span>
          </div>
          <button
            class="button expand-content is-outlined is-primary is-small"
            type="button"
            name="loadMore"
            @click="toggleDescription"
          >
            Less
          </button>
        </div>
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
  props: ['nook'],
  mounted () {
    this.checkCommentaryLength()
  },
  data () {
    return {
      commentaryOverflow: null,
      commentaryExpanded: null
    }
  },
  methods: {
    checkCommentaryLength () {
      console.log(this.nook.commentary.length)
      if (this.nook.commentary.length > 500) {
        this.commentaryOverflow = true
        this.commentaryExpanded = false
      } else {
        this.commentaryOverflow = false
      }
    },
    toggleDescription () {
      this.commentaryExpanded = !this.commentaryExpanded
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
  .expand-content
    margin-top: .5rem
    display: flex
    margin-right: auto
    margin-left: auto
</style>
