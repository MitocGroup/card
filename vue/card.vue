<template>
  <div class="jp-card-box">
    <slot name="preview">
      <div class="jp-card-preview"></div>
    </slot>
  </div>
</template>

<script>
import Card from '../src/coffee/card.coffee'

export default {
  props: {
    options: Object
  },
  
  data () {
    return {
      $card: null
    }
  },
  
  activated () {
    if (this.$card) {
      this.$card.handleInitialValues()
    }
  },
  
  mounted () {
    this.$nextTick(() => {
      this.options.container = this.options.container || '.jp-card-preview'
      
      this.$card = new Card(this.options)
    })
  }
}
</script>
