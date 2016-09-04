<template>
  <div id="app">
    <div class="row" v-for="i in 9">
      <cell :initial-value="seed[i][j]"
            v-for="j in 9">
      </cell>
    </div>
  </div>
</template>

<script>
import Cell from './components/Cell'

export default {
  data () {
    return {
      seed: [
        [8, null, null, 4, null, 6, null, null, 7],
        [null, null, null, null, null, null, 4, null, null],
        [null, 1, null, null, null, null, 6, 5, null],

        [5, null, 9, null, 3, null, 7, 8, null],
        [null, null, null, null, 7, null, null, null, null],
        [null, 4, 8, null, 2, null, 1, null, 3],

        [null, 5, 2, null, null, null, null, 9, null],
        [null, null, 1, null, null, null, null, null, null],
        [3, null, null, 9, null, 2, null, null, 5]

      ]
    }
  },
  components: {
    Cell
  }
}
</script>

<style lang="scss">
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: 20px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

.row {
  display: flex;
  flex-direction: row;

  &:nth-child(3n) {
    margin-bottom: 3%;
  }
}
</style>
