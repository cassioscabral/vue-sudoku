<template>
  <div id="app">
    <div class="row" v-for="row in 9">
      <!-- FIXME need key track -->
      <cell
        v-for="column in 9"
        :initial-value="seed[row][column]"
        :column="column"
        :row="row"
        :value="getGameValue(column, row)"
        :is-valid="isDuplicate(column, row, getGameValue(column, row))"
        >
      </cell>
    </div>
  </div>
</template>

<script>
import Cell from './components/Cell'

const seed = [
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

export default {
  data () {
    return {
      seed,
      game: [...seed] // FIXME
    }
  },
  components: {
    Cell
  },
  // watch: {
  //   game: {
  //     handler () { console.log('this.game') },
  //     deep: true
  //   }
  // },
  methods: {
    getGameValue (column, row) {
      return this.game[row][column]
    },
    updateGame ({column, row, value}) {
      let newGame = this.game.slice(0)
      console.log('newGame', newGame)

      newGame[row][column] = value
      // this.game[row] = [...this.game[row]]
      this.game = newGame
    },
    isDuplicate (column, row, cellValue) {
      if (!cellValue) {
        return true
      }
      let gameRow = this.game[row]
      // console.log('row', gameRow)
      // debugger
      let result = !gameRow.some((item, index) => { return (item === cellValue) && (index !== column) })
      console.log('result', result)
      return result
    }
  },
  events: {
    updatedCellValue (data) {
      // console.log(data)
      // update game
      this.updateGame(data)
    }
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
