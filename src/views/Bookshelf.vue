<template>
  <div>
    <div class="page-title">
      <h1 class="title is-2">
        The Bookshelf
      </h1>
      <h5 class="subtitle">
        Past and present.
      </h5>
    </div>
    <div class="bookshelf" v-for="result in results" :key="result.uuid">
      <h4 class="title is-4">{{ result.featured_date }}</h4>
      <div class="columns is-mobile">
        <div class="column is-narrow">
          <div class="img-box">
            <div class="">  ^^^^^  </div>
            <div class="">(  o o )</div>
            <div class=""> --- </div>
          </div>
        </div>
        <div class="column is-full">
          <div class="title-box">
            <div class="has-text-weight-bold">
              {{ result.title }}
            </div>
            <div v-if="result.sub_title !== null">
              {{ result.sub_title }}
            </div>
          </div>
          <div class="info-box">
            <div class="author">
              <div class="info-label has-text-grey">
                <span v-if="result.authors.length > 1">authors: </span>
                <span v-else>author: </span>
              </div>
              <span v-for="author in result.authors" :key="author.full_name">{{ author.full_name }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="description">
        <div class="">
          Overview
        </div>
        <div class="">
          {{ apiRes.volumeInfo.description }}
        </div>
      </div>
      <!-- <div class="columns">
        <div class="columm">
          <img alt="Bean Books" src="../assets/bean.png">
        </div>
        <div class="column">

        </div>
      </div> -->
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      apiRes: [],
      results: [],
      res: {
        count: 4,
        next: null,
        previous: null,
        results: [
          {
            uuid: '370e4963-53a3-4d2c-be98-16e39283499d',
            created_on: '2019-11-18T01:07:26.534330Z',
            updated_on: '2019-11-18T01:07:26.534366Z',
            title: 'War and Peace',
            sub_title: 'The story of War and Peace',
            authors: [
              { full_name: 'Leo Tolstoy' }
            ],
            release_date: '1869-01-01',
            categories: [
              { name: 'fiction' },
              { name: 'history' }
            ],
            isbn_10: '9780854566242',
            isbn_13: null,
            featured_date: '2019-10-01',
            rating: null,
            commentary: null
          },
          {
            uuid: '8b5dfc0c-dee0-4472-89a8-e99943f0979e',
            created_on: '2019-11-18T01:07:26.540603Z',
            updated_on: '2019-11-18T01:07:26.540672Z',
            title: 'War and Peace',
            sub_title: null,
            authors: [
              { full_name: 'Leo Tolstoy' }
            ],
            release_date: '1869-01-01',
            categories: [
              { name: 'fiction' },
              { name: 'history' }
            ],
            isbn_10: '9780854566242',
            isbn_13: null,
            featured_date: '2019-09-01',
            rating: null,
            commentary: null
          },
          {
            uuid: '2fa59135-6130-4f6b-aa4f-27d6a092fea2',
            created_on: '2019-11-18T01:07:26.546379Z',
            updated_on: '2019-11-18T01:07:26.546415Z',
            title: 'War and Peace',
            sub_title: null,
            authors: [
              { full_name: 'Leo Tolstoy' }
            ],
            release_date: '1869-01-01',
            categories: [
              { name: 'fiction' },
              { name: 'history' }
            ],
            isbn_10: '9780854566242',
            isbn_13: null,
            featured_date: '2019-08-01',
            rating: null,
            commentary: null
          },
          {
            uuid: '6a86bb8c-7329-4504-8782-08405d283419',
            created_on: '2019-11-18T01:07:26.554086Z',
            updated_on: '2019-11-18T01:07:26.554137Z',
            title: 'War and Peace',
            sub_title: null,
            authors: [
              { full_name: 'Leo Tolstoy' }
            ],
            release_date: '1869-01-01',
            categories: [
              { name: 'fiction' },
              { name: 'history' }
            ],
            isbn_10: '9780854566242',
            isbn_13: null,
            featured_date: '2019-07-01',
            rating: null,
            commentary: null
          }
        ]
      }
    }
  },
  mounted () {
    this.results = this.res.results
    this.getGoogleApi()
  },
  methods: {
    getBook () {
      window.alert('hello')
    },
    async getGoogleApi () {
      const res = await axios.get('https://www.googleapis.com/books/v1/volumes/dXewCgAAQBAJ')
      this.apiRes = res.data
    }
  }
}
</script>

<style lang="sass" scoped>
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
    display: flex
    flex-direction: column
    align-items: flex-start
    justify-content: flex-start
  .info-box
    display: flex
    flex-direction: column
    align-items: flex-start
    .author
      display: flex
  .info-label
    padding-right: .5rem
  .column
    // background-color: #000
  .description
    display: flex
    flex-direction: column
    align-items: flex-start
</style>
