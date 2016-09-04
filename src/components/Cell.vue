<template lang="html">
  <input
    v-if="initialValue"
    type="number" min="1" max="9" :value="initialValue" disabled/>
  <input
    v-else
    type="number" min="1" max="9" v-model="value"/>
</template>

<script>
export default {
  props: {
    initialValue: {
      type: Number,
      default: null
    }
  },
  data () {
    return {
    }
  },
  computed: {},
  ready () {},
  attached () {},
  methods: {},
  components: {}
}
</script>

<style lang="css">
</style>
