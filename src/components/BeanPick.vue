<template>
  <div>
    <div class="bookshelf">
      <h4 class="title is-4 has-text-primary">
        {{ format(new Date(result.featured_date), 'MMMM') }}
        {{ `'${format(new Date(result.featured_date), 'yy')}` }}
      </h4>
      <div class="columns">
        <div class="img column is-narrow">
          <figure class="image">
            <img alt="Pick" :src="thumbnail" v-if="thumbnail">
            <bean-cursor v-else/>
          </figure>
        </div>
        <div class="column is-full">
          <div class="title-box">
            <span class="has-text-weight-bold has-text-primary">
              {{ `"${result.title}"` }}
            </span>
            <span v-for="author in result.authors" :key="author.full_name">{{ `by ${author.full_name}` }}</span>
          </div>
          <div class="info-box">
            <div class="categories">
              <div class="columns is-mobile is-variable is-1">
                <div class="column is-narrow">
                  <span class="info-label has-text-left has-text-grey">genres:</span>
                </div>
                <div class="column">
                  <div class="tags">
                    <div class="tag is-primary is-light has-text-weight-bold is-lowercase"
                      v-for="category in result.categories"
                      :key="category.name">
                      {{ category.name }}
                    </div>
                  </div>
                </div>
              </div>

            </div>
          </div>
        </div>
      </div>
      <div class="description">
        <div v-if="apiRes.volumeInfo">
          <div v-if="descriptionOverflow">
            <div v-if="!descriptionExpanded">
              <span class="book-description" v-html="this.description.slice(0,500)"></span><span>...</span>
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
              <span class="book-description" v-html="this.description"></span>
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
          <div v-else>
            <span class="book-description" v-html="this.description"></span>
          </div>
        </div>
        <bean-cursor v-else/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import BeanCursor from '@/components/BeanCursor.vue'
import { format } from 'date-fns'

export default {
  props: ['result'],
  components: {
    BeanCursor
  },
  data () {
    return {
      format,
      apiRes: {},
      thumbnail: null,
      smallThumbnail: null,
      descriptionOverflow: null,
      descriptionExpanded: null
    }
  },
  created () {
    this.getGoogleApi()
  },
  methods: {
    getDescription () {
      this.description = this.apiRes.volumeInfo.description
      this.checkDescriptionLength()
    },
    checkDescriptionLength () {
      if (this.description.length > 500) {
        this.descriptionOverflow = true
        this.descriptionExpanded = false
      } else {
        this.descriptionOverflow = false
      }
    },
    toggleDescription () {
      this.descriptionExpanded = !this.descriptionExpanded
    },
    setThumnails () {
      const { imageLinks } = this.apiRes.volumeInfo
      this.smallThumbnail = imageLinks.smallThumbnail
      this.thumbnail = imageLinks.thumbnail
    },
    async getGoogleApi () {
      try {
        const response = await axios.get(`https://www.googleapis.com/books/v1/volumes?q=${this.result.isbn_10}`)
        this.apiRes = response.data.items[0]
        this.setThumnails()
        this.getDescription()
      } catch (error) {
        // handle error
      }
    }
  }
}
</script>

<style lang="sass" scoped>
  @import "@/sass/custom.sass"
  @import "~bulma/bulma"
  +until(550px)
    .columns
      width: 100%
    .img
      display: flex
      justify-content: center
  .bookshelf
    display: flex
    flex-direction: column
    align-items: flex-start
    margin-bottom: 2rem
  .img-box
    display: flex
    flex-direction: column
    border: 1px solid #000
    align-items: center
    justify-content: center
    width: 200px
    height: 200px
  .title-box
    text-align: left
  .info-box
    display: flex
    flex-direction: column
    align-items: flex-start
    .author
      display: flex
  .info-label
    padding-right: .5rem
  .categories
    width: 100%
  .description
    display: flex
    flex-direction: column
    align-items: flex-start
  .book-description
    text-align: left
  .tag
    margin-right: 0.5rem
    margin-bottom: .5rem
  .wrap
    display: flex
    flex-wrap: wrap
  .expand-content
    margin-top: .5rem
    display: flex
    margin-right: auto
    margin-left: auto
</style>
