<template lang="html">
  <div class="item">
    <input
      v-if="initialValue"
      type="text" pattern="[1-9]" :value="initialValue" disabled/>
    <input
      v-else
      type="text" pattern="[1-9]" v-model="value"/>
  </div>

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
      value: null
    }
  },
  computed: {},
  ready () {},
  attached () {},
  methods: {},
  components: {}
}
</script>

<style lang="scss">
.item {

  &:nth-child(3n) {
    margin-right: 3%;
  }

  input {
    width: 40px;
    height: 40px;
    font-size: 2rem;
    text-align: center;
    display: inline-block;
    border: 1px solid #e1e1e1;
    padding: 0;

    &[disabled] {
      background-color: #e3e3e3;
    }

    &:focus {
      outline: none;
      background-color: darken(#FFF, 3%);
    }
  }
}
</style>
