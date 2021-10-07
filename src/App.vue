<template>
 <h1>Ninja Reaction app</h1>
 <button  @click="start"  :disabled="isPlaying">Click to Play! ( {{isPlaying}}  and deplay {{delay}})</button>
<block v-if="isPlaying" :delay="delay" @endTime="endGame"></block>
results 

<results v-if="showResult && !isPlaying" :score="score" ></results>
</template>


<script>
import block from './components/block.vue'
import results from './components/results.vue'

export default {
  name: 'App',
  components: { block , results},
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResult:false
      }
  },

  methods:  {
    start(){
      this.isPlaying=!this.isPlaying,
      this.delay=2000 +Math.random()*5000,
      
      console.log(this.delay)
    },

    endGame(reactionTime){
      this.score=reactionTime
      this.isPlaying=!this.isPlaying
      this.showResult=true

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
</style>
