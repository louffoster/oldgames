<template>
   <div>
      <div id="lwgame"></div>
   </div>
</template>

<script setup>
import Phaser from "phaser"
import Menu from "@/games/latticewords/main_menu"
import Latticewords from "@/games/latticewords/main"
import { onMounted, onUnmounted } from "vue"

function initGame() {
   var config = {
      type: Phaser.AUTO,
      scale: {
         parent: "lwgame",
         mode: Phaser.Scale.FIT,
         width: 460,
         height: 550,
      },
      backgroundColor: "3F51B5",
      title: "LatticeWords",
      scene: [Menu, Latticewords],
   }
   window.game = new Phaser.Game(config)
}

onMounted(() => {
 initGame()
})
onUnmounted(() => {
   window.game.destroy(true)
})
</script>

<style scoped>
#lwgame {
   margin: 0 0;
   display: flex;
   flex-flow: row nowrap;
   justify-content: center;
}
@media only screen and (min-width: 768px) {
   #lwgame {
      height: auto;
   }
}
@media only screen and (max-width: 768px) {
   #lwgame {
      max-height: 550px;
   }
}
</style>

