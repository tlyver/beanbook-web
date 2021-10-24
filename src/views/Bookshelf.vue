<template>
  <div>
    <div class="page-title">
      <h1 class="title is-2 has-text-primary">
        The Bookshelf
      </h1>
      <h5 class="subtitle has-text-warning">
        Past and present.
      </h5>
    </div>
    <div class="page-description">
      <p>
        Stay up to date on what we are reading in the club! Every month, a different member selects the novel and facilitates our discussion during the meeting. Here you can find past and current picks!
      </p>
      <p style="margin-top: 1rem; font-style: italic; font-size: .75rem">
        I am an affiliate of Bookshop.org and I will earn a commission if you click through and make a purchase.
      </p>
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
        const res = await axios.get('api/club/books/')
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
