<template>
  <h1>Ninja reaction timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results :score="score" v-if="showResults"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',

  components:{Block,Results} ,
  
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults : false
    }
  },
  methods:{
     start(){
       this.delay = 2000 + Math.random() *5000
       this.isPlaying = true
       this.showResults=false
      //  console.log(this.delay)

     },
     endGame(reactionTime){
       this.score = reactionTime
       this.isPlaying= false  
       this.showResults = true

     }
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
  background: palevioletred;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 20px;
  letter-spacing: 1px;
  padding: 8px 16px;
  margin: 10px;

}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;

}
</style>
