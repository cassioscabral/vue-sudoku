<template lang="html">
  <div class="item">
    <input
      type="text" pattern="[1-9]"
      v-model="value"
      @change="dispatchUpdateCellValue"
      :disabled="initialValue"
      :value="initialValue"
      :class="{
        'is-valid': isValid
      }"
      />
  </div>

</template>

<script>
export default {
  props: {
    initialValue: {
      type: Number,
      default: null
    },
    // index from 0 to 8
    column: {
      type: Number,
      required: true
    },
    // index from 0 to 8
    row: {
      type: Number,
      required: true
    },
    value: {
      type: Number,
      default: null
    },
    isValid: {
      type: Boolean
    }
  },
  data () {
    return {
    }
  },
  computed: {},
  ready () {},
  attached () {},
  methods: {
    dispatchUpdateCellValue () {
      this.$dispatch('updatedCellValue', {
        value: Number(this.value),
        column: this.column,
        row: this.row
      })
    }
  },
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
    background-color: red;

    &.is-valid {
      background-color: transparent;
    }

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
