<template lang="html">
  <div>
    <p>{{conditionalMessage}}</p>
  </div>
</template>

<script>
export default {
  name: 'conditionalComponent',
  props: ['conditionalMessage'],
  data () {
    return {
    }
  }
}
</script>

<style lang="css">
</style>
