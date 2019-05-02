<template>
    <div>
        <div class="alert alert-warning text-center" v-if="!checkCorrectness">
            <h1>Oops! Wrong</h1>
            <hr>
            <button class="btn btn-primary" @click="next">Try Again</button>
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
           next() {
               this.$emit('next');         
           }
       }
    }
</script> 