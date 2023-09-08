<template>
  <div id="app">
    <h1>เกมเป่ายิ้งงงงงฉุบ</h1>
    <GameComponent />
  </div>

</template>

<script>
import GameComponent from './components/HelloWorld.vue';

export default {
  components: {
    GameComponent,
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #000000;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

h1 {
  font-size: 3em;
  margin-bottom: 20px;
}

.gameplayer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px;
}

.reset-button {
  background-color: #e1fa3f;
  color: #ffffff;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 1.2em;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.start-button {
  background-color: #ff6905;
  color: #fff;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 1.2em;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.start-button:hover,
.reset-button:hover {
  background-color: #ff4c00;
}

.score-game {
  background-color: #ffffff;
  color: #000000;
  padding: 10px;
  margin: 20px;
  text-align: center;
  border-radius: 25px;
  border: 2px solid #ff1818;
  max-width: 300px;
}

.score {
  margin: 0;
  font-size: 1.5em;
}
</style>
