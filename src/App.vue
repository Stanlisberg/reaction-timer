<template>
  <div class='container'>
    <!-- <h1>{{ title }}</h1> 
    <input type='text' ref='data' />
    <p>Welcome...</p> -->

    <div :style="{display: 'flex', justifyContent:'center'}">
     <button @click='toggleModal'>Open First Modal</button>
     <button :style="{marginLeft: '10px'}" @click='toggleModalTwo'>Open Second Modal</button>
    </div>
    <div v-if='!showModal'>
      <Modal theme='sale' @close='toggleModal'>

        <!-- For slot exapmle 1-->
        <h1>This is the first Modal!</h1>
        <p>A result oriented Web developer</p>

        <!-- For Named slot example 1-->
        <template v-slot:link>
          <a href='#'>Sign up now</a>
          <a href='#'>More info</a>
        </template>
      </Modal>
    </div>
    <div v-if='!showModalTwo'>
      <Modal @close='toggleModalTwo'>

        <h1>This is the second modal!</h1>
        <p>What do you have for us today?</p>

      </Modal>
    </div>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  data() {
    return {
      // title: 'This is my first vue App',
      // message: 'Sign up for your news letter',
      // email:'stanlisberg@gmail.com',
      showModal: true,
      showModalTwo: true
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.data)
      this.$refs.data.classList.add('active')
      this.$refs.data.focus()
    },
    toggleModal() {
        this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo 
    }
  },

  //---------For rendering components
  components: { Modal }
}
</script>


<style scoped>

.container {
  margin: 100px auto;
  border: 1px solid black;
  text-align: center;
  padding:20px 0;
}
