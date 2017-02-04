<template lang="html">
  <div>
    <p>{{conditionalMessage}}</p>
  </div>
</template>

<script>
export default {
  name: 'conditional component',
  data () {
    return {
      conditionalMessage: 'Here I am!'
    }
  }
}
</script>

<style lang="css">
p {
  font-size: 2em
}
</style>
