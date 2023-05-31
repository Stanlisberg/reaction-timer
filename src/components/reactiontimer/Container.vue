<template>
  <div class='container' v-if='stopDelay' @click='stopGame'>
    <p>Click Me</p>
  </div>

</template>

<script>
export default {
 props: ['delay'],
    data() {
        return {
            timer: null,
            stopDelay: false,
            reactionTime: 0
       }
    },
    mounted() {
        setTimeout(() => {
            this.stopDelay = true
            this.startGame()
         }, this.delay)

         console.log(this.reactionTime)
    },   
    methods: {
          startGame() {
          this.timer = setInterval(() => {
            this.reactionTime += 10
           }, 10)
        },
        stopGame() {
           this.$emit('end', this.reactionTime)
           console.log(this.reactionTime)
           clearInterval(this.timer);
        }
    },
    
}
</script>

<style>
.container {
  width: 350px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 80px 0;
  margin-top: 40px;
  margin-bottom: 40px;
  /* margin-left: 20px;
  margin-right: 20px; */

}

p{
    font-weight: 800
}
</style>