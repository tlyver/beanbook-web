<template>
  <div>
    <div class="page-title">
      <h1 class="title is-2 has-text-primary">
        The Bookshelf
      </h1>
      <h5 class="subtitle has-text-primary">
        Past and present.
      </h5>
    </div>
    <bean-pick v-for="result in results" :key="result.uuid" :result="result"/>
  </div>
</template>
<script>
import axios from 'axios'
import BeanPick from '@/components/BeanPick.vue'

export default {
  components: {
    BeanPick
  },
  data () {
    return {
      results: []
      // res: {
      //   count: 4,
      //   next: null,
      //   previous: null,
      //   results: [
      //     {
      //       uuid: '370e4963-53a3-4d2c-be98-16e39283499d',
      //       created_on: '2019-11-18T01:07:26.534330Z',
      //       updated_on: '2019-11-18T01:07:26.534366Z',
      //       title: 'War and Peace',
      //       sub_title: 'The story of War and Peace',
      //       authors: [
      //         { full_name: 'Leo Tolstoy' }
      //       ],
      //       release_date: '1869-01-01',
      //       categories: [
      //         { name: 'fiction' },
      //         { name: 'history' }
      //       ],
      //       isbn_10: '0156787334',
      //       isbn_13: null,
      //       featured_date: '2019-10-01',
      //       rating: null,
      //       commentary: null
      //     }
      //   ]
      // }
    }
  },
  mounted () {
    this.getBooks()
    this.results = this.res.results
  },
  methods: {
    async getBooks () {
      try {
        const res = await axios.get('beanbook.club/api/club/books')
        console.log(res)
        this.results = res.data
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
