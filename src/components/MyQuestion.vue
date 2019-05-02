<template>
    <div class="panel panel-default">
        <div class="panel-heading">
            <h3 class="panel-title text-center">Answer this: {{ question }}</h3>
        </div>
        <div class="panel-body  text-center">
            <div class="col-xs-12 col-sm-6 col-sm-offset-3 text-center">
                <label>Type in your answer:</label>
                <input v-model="yourAnswer">
            </div>
            <hr>
            <br>
            <button class="btn btn-primary" @click="checkAnswer">Check Answer</button>
        </div>
    </div>
</template> 

<script>
import { Bus } from '../main.js';

export default {
    props: [ 'sameQuestion'],
    data() {
        return {
            yourAnswer: '',
            firstNumber: 0,
            secondNumber: 0,
            question: "",
            operation: 0,
            correctAnswer: "",
            formerQuestion: "",
            test: 'dufhrdgfkuefb'
        }
    },
    methods: {
        createQuestion() {
           
                this.firstNumber = this.generateRandomNumber(10,50);
                this.secondNumber = this.generateRandomNumber(5, 30);
                this.operation = this.generateRandomNumber(1,2);
                switch(this.operation) {
                    case 1: {
                        this.question = `${this.firstNumber} + ${this.secondNumber}`;
                        this.correctAnswer = this.firstNumber + this.secondNumber;
                        break
                    }
                    case 2: {
                        this.question = `${this.firstNumber} - ${this.secondNumber}`;
                        this.correctAnswer = this.firstNumber - this.secondNumber;
                        break
                    }
                }
                this.formerQuestion = this.question
                console.log('check same quwstion2 >> ',this.formerQuestion)

        },
        generateRandomNumber(min,max) {
            return Math.round(Math.random() * (max-min) + min);
        },
        checkAnswer() {
            console.log('show correct  >>> ',this.correctAnswer);
            
            if(this.yourAnswer == this.correctAnswer) {
                this.createQuestion();
                console.log('show correct new >>> ',this.correctAnswer);
                this.yourAnswer = ''
                this.$emit('rightAnswer');
            }
            else{
                this.$emit('wrongAnswer');
            }
        }
    },
    mounted() {        
        console.log('show test >> ',this.test)
        this.createQuestion();
    }
}
</script>

<style>

</style>

