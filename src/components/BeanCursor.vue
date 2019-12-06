<template>
  <font-awesome-icon v-if="showIcon" icon="i-cursor" />
  <font-awesome-icon v-else class="has-text-white" icon="i-cursor" />
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import {
  faICursor
} from '@fortawesome/free-solid-svg-icons'

library.add(
  faICursor
)

export default {
  name: 'BeanCursor',
  data () {
    return {
      showIcon: true
    }
  },
  mounted () {
    this.iconCounter()
  },
  methods: {
    toggleIcon () {
      this.showIcon = !this.showIcon
      this.iconTimer()
    },
    iconTimer () {
      setTimeout(this.toggleIcon, 400)
    }
  }
}
</script>
