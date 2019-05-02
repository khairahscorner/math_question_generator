<template>
    <div class="container">
        <div class="row" style="margin-top: 15vh">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1 class="text-center">Basic Quiz</h1>
            </div>
        </div>
        <hr>
        <!-- My own game -->
        <div class="row">
            <br>
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <transition name="flip" mode="out-in">
                <keep-alive >
                    <component 
                    :is="option" 
                    @rightAnswer="rightAnswer" 
                    @wrongAnswer="wrongAnswer"
                    :checkCorrectness="checkCorrectness"
                    :sameQuestion="sameQuestion"
                    @next="next"
                    ></component>
                </keep-alive> 
                </transition> 
            </div>
        </div>
    </div>
</template>

<script>
    import MyQuestion from './components/MyQuestion.vue';
    import RightAnswer from './components/rightAnswer.vue';
    import WrongAnswer from './components/wrongAnswer.vue';
    import { Bus } from './main.js'
    export default {
        data() {
            return {
                option: 'app-my-question',
                checkCorrectness: true,
                sameQuestion: false
            }
        },
        methods: {
            wrongAnswer() {
                this.checkCorrectness = false;
                this.sameQuestion = true
                this.option = 'app-wrong-answer';
            },
            rightAnswer() {
                this.checkCorrectness = true;
                this.sameQuestion = false
                this.option = 'app-right-answer';
            },
            next() {
                this.option = 'app-my-question';
            }
        },
        components: {
            appMyQuestion: MyQuestion,
            appRightAnswer: RightAnswer,
            appWrongAnswer: WrongAnswer
        }
    }
</script>

<style>
    .flip-enter-active {
        animation: flip-in  0.2s ease-out forwards;
    }
    .flip-leave-active{
        animation: flip-out  0.2s ease-out forwards;
    }
    @keyframes flip-out {
        from {
            transform: rotateY(0deg);
        }
        to {
            transform: rotateY(90deg);
        }
    }
        @keyframes flip-in {
        from {
            transform: rotateY(90deg);
        }
        to {
            transform: rotateY(0deg);
        }
    }
</style>

