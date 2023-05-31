<template>
   <div class='score'>React Time:{{ score }} ms</div>
   <p class='text'>{{ message }}</p>
</template>

<script>

export default{
   props: ['score'],
   data() {
      return{
        message: ''
      }
   },
   mounted() {
      if(this.score < 250) {
         this.message = 'Fast Fingers'
      } else if(this.score < 400) {
         this.message = 'Rapid Reflexes'
      } else {
         this.message = 'Snail Pace...'
      }
   }

} 

</script>

<style>
 .score{
    font-weight:800;
 }
 span{
    color: lightslategray
 }

 .text {
    color: teal;
    font-weight: bold;
    font-size: 1.4em;
 }
</style>