<template>
  <div id="app">
    <div class="stopwatches-container">
      <div class="stopwatch" v-for="timer in timers" :key="timer.id">
        <StopwatchTimer :timer="timer" />
      </div>
      <button @click="addStopwatch" class="add-button">
        <i class="fas fa-plus"></i>
      </button>
    </div>
  </div>
</template>

<script>
import StopwatchTimer from "./components/StopwatchTimer.vue";

export default {
  name: "App",
  components: {
    StopwatchTimer,
  },
  data() {
    return {
      timers: [{ id: 1, time: 0, running: false, paused: false }],
      lastId: 1,
      gridRowCount: 1, // Счетчик количества строк сетки
    };
  },
  methods: {
  addStopwatch() {
    const newTimer = {
      id: this.lastId + 1,
      time: 0,
      running: false,
      paused: false,
    };
    this.timers.push(newTimer);
    this.lastId++;
    this.gridRowCount = Math.ceil(this.timers.length / 3); // Определяем количество строк сетки
    
  },
},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

html {
  background-color: #353638;
}

.stopwatches-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(135px, auto);
  grid-gap: 45px;
  width: 800px;
  margin: 0 auto;
}

.stopwatch {
  position: relative;
}

.add-button {
  height: 135px;
  width: 225px;
  background-color: #696969;
}

.fa-plus {
  color: #9E9E9E;
  font-size: 1.5em;
}

.stopwatch:nth-child(3n + 1) .add-button {
  position: absolute;
  bottom: 0;
  left: 0;
}

.stopwatch:nth-child(3n + 2) .add-button {
  position: absolute;
  bottom: 0;
  left: calc(33.33% + 22.5px);
}

.stopwatch:nth-child(3n + 3) .add-button {
  position: absolute;
  bottom: 0;
  left: calc(66.66% + 45px);
}


@media screen and (min-width: 768px) and (max-width: 1023px) {
  .stopwatches-container {
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: minmax(135px, auto);
    grid-gap: 45px;
    width: 500px;
  }

  .stopwatch:nth-child(2n + 1) .add-button {
    position: absolute;
    bottom: 0;
    left: 0;
  }

  .stopwatch:nth-child(2n + 2) .add-button {
    position: absolute;
    bottom: 0;
    left: calc(50% + 22.5px);
  }
}

@media screen and (min-width: 320px) and (max-width: 768px) {
  .stopwatches-container {
    grid-template-columns: repeat(1, 1fr);
    grid-auto-rows: minmax(135px, auto);
    justify-content: center;
    grid-gap: 45px;
    width: 210px;
    height: 120px;
  }

  .stopwatch:nth-child(n) .add-button {
    position: absolute;
    bottom: 0;
    left: 0;
  }
  
  .stopwatch {
    margin-bottom: 45px;
  }
}


</style>
