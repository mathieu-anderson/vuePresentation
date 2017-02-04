<template lang="html">
  <div>
    <p>{{ message }}</p>
    <input v-model="message">
    <button v-on:click="renderComponent">Render conditional component</button>
    <conditionalComponent
    v-if="render"
    v-bind:conditionalMessage="conditionalMessage"
    />
  </div>
</template>

<script>
import conditionalComponent from './conditionalComponent'
export default {
  name: 'componentDemo',
  components: {
    conditionalComponent
  },
  data () {
    return {
      message: 'V-model is awesome',
      render: false,
      conditionalMessage: 'Here I am!'
    }
  },
  methods: {
    renderComponent: function () {
      this.render = !this.render
    }
  }
}
</script>

<style lang="css">
p {
  font-size: 1em
}
</style>
