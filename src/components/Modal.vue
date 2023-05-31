<template>
  <div class='backdrop' @click.self='closeModal'>
    <div class='modal' :class="{sale: theme === 'sale'}">
        <!-- Normal slot 1-->
        <slot></slot>

        <!-- Named slot 1-->
        <div class='action'>
            <slot name='link'></slot>  
        </div> 

        <!-- For props example -->
            <!-- <h1>{{ message }}</h1>
            <p>{{ email }}</p> -->
    </div>
  </div> 
</template>


<script>
export default {
//---------For redering Props--------
    props:  ['message', 'email', 'theme'], 

    data() {
        return {
        
        }     
    },
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>


<style>
h1 {
    color: teal;
}
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
    text-align:center;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}

.modal .action a {
    color:#333;
    padding: 8px;
    background:lightsalmon;
    /* border: 1px solid #eee; */
    border-radius: 5px;
    margin: 10px;
    text-decoration: none;

}

.modal.sale {
    background:lightseagreen;
}

.sale h1 {
    color: white
}
</style>