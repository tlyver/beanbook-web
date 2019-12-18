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
    }
  },
  created () {
    this.getBooks()
  },
  methods: {
    async getBooks () {
      try {
        const res = await axios.get('api/club/books')
        this.results = res.data.results
      } catch (error) {
        // handle error
      }
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
