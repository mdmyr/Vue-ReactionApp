<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <p>{{DisplayTimer}}ms</p>
    <p>click me </p>
  </div>
</template>

<script>


export default {
    props:['delay',],

    mounted(){
        console.log("#block component mounted")
        console.log("delay prop value :" + this.delay)
        console.log("executing a custom method:")

        setTimeout(()=>{
          this.showBlock=true
          this.startTimer()       
        },this.delay)

        
    },
    updated(){
        console.log("Update has fired : " + this.delay)
    },

    unmounted(){
        console.log("unmounted.")
    },
    
    //data 
    data(){
        return{
            showBlock:false,
            timer:this.delay,
            totaltime:null,
            reactionTime:0,
            DisplayTimer:0
        }
    },
    //methods

    methods:{
        //start timer
    startTimer(){
         
         this.totaltime = setInterval(()=>{
             this.DisplayTimer +=10
         },10)
    },
        // stop timer
    stopTimer(){
      this.$.emit('endTime',this.DisplayTimer)
      clearInterval(this.totaltime)
    },
    stopDisplay(){
       // this.DisplayTimer=this.totaltime
        //setInterval(null)
    }
    
   }
}
</script>

<style>
.block{ 
    width: 400px;
    border-radius: 20px;
    background:#0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>