<template>
    <div>
        <!-- <p>hrfjbjvhudjfbvudjfbnvdjxncsj</p> -->
        <div class="alert alert-success text-center" v-if="checkCorrectness">
            <h1>That's Correct!</h1>
            <hr>
            <button class="btn btn-primary" @click="nextQuestion">Next Question</button>
        </div>
       
   </div> 
</template>
<style>

</style>
<script>
import { Bus } from '../main.js';
    export default{
       props: ['checkCorrectness'],
       methods: {
           nextQuestion() {
               this.$emit('next');
           }
       }
    }
</script> 