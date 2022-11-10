<template>
  <h1>VUE JS Reaction Timer</h1>

  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score ="score"/>
  
  
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {Block,Results},
  data(){
    return{
      isPlaying:false,
      delay: null,
      score:null,
      showResults:false,
    }
  },

  methods:{
    start(){
      this.delay = 500 + Math.random()*5000
      this.isPlaying = true
      this.showResults = false

    },
    endGame(reactiontime){
      this.score = reactiontime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
*{
  background-color: black;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
body{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button{
  background: red;
  color: white;
  border: none;
  border-radius: 5px;
  letter-spacing: 2px;
  cursor:pointer;
  padding: 10px 25px;
}

button[disabled]{
  opacity:0.2;
  cursor:not-allowed;
}
</style>
