<template>
  <h1>Reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="show" :score="score"/>
  
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block, Results
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      show: false,
    }
  },
  methods:{
    start(){
      this.delay= 2000 + Math.random() * 5000
      this.isPlaying=true
      this.show=false
    },
    endGame(reactionTime){
      this.score=reactionTime
      this.isPlaying=false
      this.show=true
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button{
  padding: 10px 15px;
  letter-spacing: 1px;
  border: none;
  background: rgb(36, 172, 108);
  font-weight: bold;
  color: white;
  border-radius: 10px;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
