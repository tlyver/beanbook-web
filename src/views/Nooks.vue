<template>
  <div>
    <div class="page-title">
      <h1 class="title is-2 has-text-primary">
        Nooks
      </h1>
      <h5 class="subtitle has-text-primary">
        From all corners.
      </h5>
    </div>
    <bean-nook v-for="nook in nooks" :key="nook.uuid" :nook="nook"/>
  </div>
</template>

<script>
import axios from 'axios'
import BeanNook from '@/components/BeanNook.vue'

export default {
  components: {
    BeanNook
  },
  data () {
    return {
      nooks: []
    }
  },
  mounted () {
    this.getNooks()
  },
  methods: {
    async getNooks () {
      try {
        const res = await axios.get('api/club/nooks')
        this.nooks = res.data.results
      } catch (error) {
        // handle error
      }
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
