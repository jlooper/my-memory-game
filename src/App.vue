<template>
  <h1>Memory Game</h1>
  <main>
    <GameBoard />
  </main>
</template>

<script>
import GameBoard from "./components/GameBoard.vue";

export default {
  name: "App",
  components: {
    GameBoard: GameBoard,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  min-height: 100vh;
  background: #6563FF;
}

h1 {
  text-align: center;
  margin: 30px 0 20px;
  width: 100%;
  color: #fff;
}

main {
  display: flex;
  align-items: center;
  justify-content: center;
}

.game-board {
  padding: 25px;
  border-radius: 10px;
  background: #F8F8F8;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.cards,
.card,
.view {
  display: flex;
  align-items: center;
  justify-content: center;
}

.cards {
  height: 400px;
  width: 400px;
  flex-wrap: wrap;
  justify-content: space-between;
}

.cards .card {
  cursor: pointer;
  list-style: none;
  user-select: none;
  position: relative;
  perspective: 1000px;
  transform-style: preserve-3d;
  height: calc(100% / 4 - 10px);
  width: calc(100% / 4 - 10px);
}

.you-win-msg {
  width: 100%;
  text-align: center;
}

.you-win-msg h2 {
  font-size: 4rem;
  color: #6563FF;
}

.cards .you-win-msg {
  display: none;
}

.cards.hide .card {
  visibility: hidden;
}

.cards.hide .you-win-msg {
  display: block;
}

.card .view {
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 7px;
  background: #fff;
  pointer-events: none;
  backface-visibility: hidden;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.25s linear;
}

.card .front-view img {
  width: 19px;
}

.card .back-view img {
  max-width: 45px;
}

.card .back-view {
  transform: rotateY(-180deg);
}

.card.flip .back-view {
  transform: rotateY(0);
}

.card.flip .front-view {
  transform: rotateY(180deg);
}

.card.shake {
  animation: shake 0.35s ease-in-out;
}

@keyframes shake {
  0%,
  100% {
    transform: translateX(0);
  }
  20% {
    transform: translateX(-13px);
  }
  40% {
    transform: translateX(13px);
  }
  60% {
    transform: translateX(-8px);
  }
  80% {
    transform: translateX(8px);
  }
}

@media screen and (max-width: 700px) {
  .cards {
    height: 350px;
    width: 350px;
  }

  .card .front-view img {
    width: 17px;
  }

  .card .back-view img {
    max-width: 40px;
  }
}

@media screen and (max-width: 530px) {
  .cards {
    height: 300px;
    width: 300px;
  }

  .card .front-view img {
    width: 15px;
  }

  .card .back-view img {
    max-width: 35px;
  }
}

.console {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button,
.match-count {
  margin: 20px 0 0;
  background-color: white;
  border: 3px solid #6563ff;
  border-radius: 7px;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  padding: 8px;
  font-size: 1rem;
}

button:hover,
.match-count {
  background-color: #6563ff;
  color: white;
}

.match-count {
  cursor: default;
}
</style>
