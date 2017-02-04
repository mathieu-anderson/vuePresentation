<template lang="html">
  <div>
    <p>{{ message }}</p>
    <input v-model="message">
    <button v-on:click="renderComponent">Render conditional component</button>
    <!-- <conditionalComponent
    v-if="renderConditionalComponent"
    v-bind:conditionalMessage="conditionalMessage"
    /> -->
  </div>
</template>
<!-- v-bind:conditionalMessage="message" -->

<script>
// import conditionalComponent from './conditionalComponent'
export default {
  name: 'componentDemo',
  // components: {
  //   conditionalComponent
  // },
  data () {
    return {
      message: 'V-model is awesome',
      // renderConditionalComponent: false,
      // conditionalMessage: 'The condition is fulfilled, and so am I!'
    }
  },
  methods: {
    // renderComponent: function () {
    //   this.renderConditionalComponent = !this.renderConditionalComponent
    // }
  }
}
</script>

<style lang="css">
p {
  font-size: 1em
}
</style>
