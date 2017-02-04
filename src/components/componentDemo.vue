<template lang="html">
  <div>
    <p>{{ message }}</p>
    <input v-model="message">
    <conditionalMessage v-if="messageLength"
  </div>
</template>

<script>
export default {
  name: 'componentDemo',
  data () {
    return {
      message: 'V-model is awesome',
      conditionalMessage: 'Here I am!'
    }
  },
  methods: {
    messageLength
  }
}
</script>

<style lang="css">
p {
  font-size: 1em
}
</style>
