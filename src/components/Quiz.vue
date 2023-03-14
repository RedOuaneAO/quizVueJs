<script setup>
import {ref} from 'vue'
import Questions from '../assets/Questions.json'
const currentIndex = ref(0)
const selectedAnswer = ref('')
const correctAnswers = ref(0)
const selectAnswer = (option) => {
        selectedAnswer.value = option
      }
  
const nextQuestion = () => {
        if (selectedAnswer.value === Questions[currentIndex.value].answer) {
          correctAnswers.value++
        }
        currentIndex.value++
        selectedAnswer.value = ''
      }
  
const showResult = () => {
        if (selectedAnswer.value === Questions[currentIndex.value].answer) {
          correctAnswers.value++
        }
        alert(`You got ${correctAnswers.value} out of ${Questions.length} questions correct!`)
      }

</script>
<template>
    <div>
            <div id="progBack" class="my-2">
                <div id="progFront">
                </div>
            </div>
            <div>
                <p>Question <span>{{ Questions[currentIndex].id}}</span></p>
                <p class="fw-bold" id="questionId">{{ Questions[currentIndex].question }}</p><hr>
            </div>
            <div>
                <ul class="list-group">
                    <li class="list-group-item" v-for="option in Questions[currentIndex].options" :key="option" @click="selectAnswer(option)">
                    {{ option }}
                    </li>
                </ul>

                <div class="mt-5 d-flex justify-content-evenly">
                    <button class="btn bg-success text-white px-3" v-if="currentIndex < Questions.length - 1" @click="nextQuestion">next</button>
                    <button class="btn bg-success text-white px-3" v-else @click="showResult">Submit</button>
                </div>
            </div>
        </div>

</template>
<style scoped>
li{
    cursor: pointer;
}
#progBack {
    background-color: antiquewhite;
    width: 100%;
    height: 10px;
    border-radius: 5px;
  }

  #progFront{
    background-color: rgb(9, 50, 251);
    width: 10%;
    height: 10px;
    border-radius: 5px;
  }

</style>