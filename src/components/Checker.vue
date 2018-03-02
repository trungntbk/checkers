<template>
  <div>
    <div>
      <div v-for="player in players"> {{player}} </div>
    </div>

    <div>
      <span> Turn : </span>
      <span> {{players[activePlayer]}}  </span>
    </div>
    <div>
      <button> NEW GAME </button>
    </div>
    <div class='board'>
      <table>
        <tr v-for="rowIdx in ROW">
          <td v-for="columnIdx in COLUMN" class='cell' :class="((rowIdx + columnIdx) % 2 == 1 ? 'black': 'white')" @click="onClickCell(rowIdx, columnIdx)"></td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
// const ROW = 8;
// const COLUMN = 8;

export default {
  name: 'Checker',
  data () {
    return {
      players: [
        'Player 1',
        'Player 2'
      ],
      activePlayer: 0,
      gameState: [],
      board: [],
      ROW: 8,
      COLUMN: 8
    }
  },
  methods: {
    onClickCell() {

    },
    initializeBoard() {
      for (let i = 0; i < this.ROW; i++) {
        this.gameState[i] = [];
        for (let j = 0; j < this.COLUMN; j++) {
          this.gameState[i].splice(j, 1, 'cell-' + (j % 2 == 1 ? 'black': 'white'))
        }
      }
    },
    initializeGameState() {
      // this.gameState
      for (let i = 0; i < ROW; i++) {
        this.gameState[i] = [];
        for (let j = 0; j < COLUMN; j++) {
          this.gameState[i].splice(j, 1, {

          })
        }
      }
    }
  },
  mounted() {
    this.initializeBoard();
    this.initializeGameState();
  }
}
</script>

<style scoped>
.cell {
  width: 8vh;
  height: 8vh;
  border: 1px solid black;
  text-align: center;
}
.black {
  background: gray;
}

.white {
  background: white;
}
</style>
