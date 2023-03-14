<script setup>
import Quiz from './components/Quiz.vue'
import { ref } from 'vue';
const roles = ref(true)
const start = () => {
   roles.value = false
}
</script>
<template>
  <div class="container d-flex justify-content-center mt-5">
    <div class="text-center mt-3 bg-white p-5 rounded" style="width: 500px;">
        <div v-if="roles">
            <div>
                <h3 class="fw-bold">Rules</h3><hr>
                <ol>
                    <li class="text-start">one question is right </li>
                    <li class="text-start">if you didn't select in choice </li>
                    <li class="text-start">you cant go back to the last question after you submit</li>
                    <li class="text-start">you will get the result at the end</li>
                </ol>
            </div>
            <div class="mt-5">
                    <button class="btn bg-success text-white px-3" @click="start()">Start</button>
            </div>
        </div>
        <Quiz v-if="!roles"/>
    </div>
  </div>
</template>
<style>

</style>
