<template>
   <div class="board">
      <div class="board-edge clearfix">
         <div class="board-bondary">
            <div class="board-body">
               <div class="board-row">
                  <fieldElement :content="symbols[0]" @click="OnClicked(0)" />
                  <fieldElement :content="symbols[1]" @click="OnClicked(1)" />
                  <fieldElement :content="symbols[2]" @click="OnClicked(2)" />
               </div>
               <div class="board-row">
                  <fieldElement :content="symbols[3]" @click="OnClicked(3)" />
                  <fieldElement :content="symbols[4]" @click="OnClicked(4)" />
                  <fieldElement :content="symbols[5]" @click="OnClicked(5)" />
               </div>
               <div class="board-row">
                  <fieldElement :content="symbols[6]" @click="OnClicked(6)" />
                  <fieldElement :content="symbols[7]" @click="OnClicked(7)" />
                  <fieldElement :content="symbols[8]" @click="OnClicked(8)" />
               </div>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
import FieldElement from "./FieldElement.vue";

export default {
   name: 'Board',
   props: {
      symbols: Array,
      OnHandleClick: Function
   },
   components: {
      FieldElement
   },
   methods : {
      OnClicked(i) {
         this.OnHandleClick(i);
      }
   }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.board-row {
   clear: both;
   display: table;
}
.board-bondary {
   position: relative;
   float: left;
   left: 50%;
}
.board-body {
   position: relative;
   left: -50%;
}
.clearfix::after {
   content: "";
   display: block;
   height: 0;
   clear: both;
   visibility: hidden;
}
</style>
