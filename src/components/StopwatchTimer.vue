<template>
  <div :class="['stopwatch-container', { 'paused': !running }]">
    <div class="stopwatch" :class="{ 'paused': paused }">
      <h1 :class="{ 'paused': paused }">{{ formatTime }}</h1>
      
      <div class="buttons" :class="{ 'paused': paused }">
    <button @click="start">
      <i v-if="!running" class="fas fa-play"></i>
      <i v-else-if="!paused" class="fas fa-pause"></i>
      <i v-else class="fas fa-play"></i>
    </button>
    <button @click="reset" >
      <i class="fas fa-square"></i>
    </button>
  </div>
</div>

  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'StopwatchTimer',
  data() {
    return {
      running: false,
      paused: false,
      time: 0,
      timers: [{ id: 0, time: 0, running: false, paused: false }],
    };
  },


  computed: {
    formatTime() {
  const hours = Math.floor(this.time / 3600)
    .toString()
    .padStart(2, "0");
  const minutes = Math.floor((this.time % 3600) / 60)
    .toString()
    .padStart(2, "0");
  const seconds = (this.time % 60).toString().padStart(2, "0");

  if (hours !== "00") {
    return `${hours}:${minutes}:${seconds}`;
  } else if (minutes !== "00") {
    return `${minutes}:${seconds}`;
  } else {
    return `${seconds}`;
  }
},    
    isActive() {
      return this.running && !this.paused;
    }
  },


  
  methods: {
    start() {
      if (!this.running) {
        this.running = true;
        this.timer = setInterval(() => {
          this.time++;
        }, 1000);
      } else {
        this.paused = !this.paused;
        if (this.paused) {
          clearInterval(this.timer);
        } else {
          this.timer = setInterval(() => {
            this.time++;
          }, 1000);
        }
      }
    },

    reset() {
      this.paused = false;
      this.running = false;
      clearInterval(this.timer);
      this.time = 0;
    },
    



  },
}
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


.stopwatch {
  height: 120px;
  width: 225px;
  background-color: #696969;
  margin-right: 0;

}

.stopwatch h1 {
  border-bottom: 1px solid #ccc;
  padding-bottom: 20px;
  padding-top: 5px;
  
}

.stopwatch h1.paused {
  border-bottom-color: #b3b3b3;
  color: #969696;
}

.buttons {
  display: flex;
  justify-content: center;
  padding-top: 0px;
  align-items: center;
}

.buttons button {
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
  font-size: 1.5rem;
  margin: 0 14px;
  color: #FFFFFF;
}

.paused .buttons button {
  color: #b3b3b3;
}

@font-face {
  font-family: 'Gotham Pro';
  src: url('../assets/fonts/GothamPro.woff') format("woff"),
      url('../assets/fonts/GothamPro.woff2') format("woff2");
  font-weight: normal;
  font-style: normal;
}


h1{
  font-family: "Gotham Pro", Arial, sans-serif;
  font-size: 1.375em;
  color: #FFFFFF;
}
</style>