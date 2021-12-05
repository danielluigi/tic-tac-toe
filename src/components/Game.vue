<template>
   <div class="game-body">
      <div class="game-status"> {{ gameStatus }} </div>
      <board :symbols="symbols" :OnHandleClick="OnClicked"></board>
      <button v-if="isReset" @click="reset()">Reset</button>
   </div>
</template>

<script>
import Board from "./Board.vue";

export default {
   name: 'Game',
   components: {
      Board
   },
   data: function() {
      return {
         winner: null,
         isX: true,
         symbols: Array(9).fill("")
      };
   },
   computed: {
      gameStatus: function() {
         if (this.winner === "X" || this.winner === "O") {
            return this.winner + " wins the game!";
         }	

         if (this.isX) {
            return "Next player: X";
         } else {
            return "Next player: O";
         }
      },
      isReset: function() {
         if (this.winner === "X" || this.winner === "O") {
            return true;
         }
         for (let i = 0; i < this.symbols.length; i++) {
            if (this.symbols[i] != "X" && this.symbols[i] != "O") {
               return false;
            }
         }
         return true;
      }
   },
   methods: {
      calcWinner() {
         const lines = [
            [0,1,2],
            [3,4,5],
            [6,7,8],
            [0,3,6],
            [1,4,7],
            [2,5,8],
            [0,4,8],
            [2,4,6]
         ];

         for (let i = 0; i < lines.length; i++) {
            const [a,b,c] = lines[i];
            if (this.symbols[a] && 
               this.symbols[a] === this.symbols[b] &&
               this.symbols[b] === this.symbols[c]) {
               this.winner = this.symbols[a];
               return;
            }
         }
      },
      OnClicked(i) {
         if (this.winner === "X" || this.winner === "O") {
            return;
         }
         if (this.symbols[i] === "X" || this.symbols[i] === "O") {
            return;
         }

         if (this.isX) {
            this.symbols[i] = "X";
         } else {
            this.symbols[i] = "O";
         }
         this.isX = !this.isX;
         this.calcWinner();
      },
      reset() {
         for (let i = 0; i < this.symbols.length; i++) {
            this.symbols[i] = "";
         }
         this.winner = null;
      }
   }
};
</script>

