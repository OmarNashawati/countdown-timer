<script setup>
import { ref } from 'vue';

let countdownTimerId;
let totalSeconds = ref(0);
let isStarted = ref(false);
 
function startStop () {
  isStarted.value = !isStarted.value;

  if(isStarted.value){
    start(); 
  }else{
    stop()
  }
}
  
function start() {
  countdownTimerId = setInterval(countdown,1000)    
}
  
function stop () {
  clearInterval(countdownTimerId)
}
  
function reset () {
  if(isStarted.value){
    isStarted.value = false;
    stop();
  }
  totalSeconds.value = 0;
}

function countdown () {
  totalSeconds.value ++;
  formating()
  console.log("total seconds: "+totalSeconds.value);
}

function formating() {
  let seconds = totalSeconds.value % 60; 
  let minutes = Math.floor(totalSeconds.value / 60);

  let secondsString = seconds;
  let minutesString = minutes;

  if(seconds>=0 && seconds<=9){
    secondsString = `0${seconds}`;
  }
  if(minutes>=0 && minutes<=9){
    minutesString = `0${minutes}`
  }

  console.log(minutesString+":"+secondsString);
  
  return `${minutesString}:${secondsString}`
}

</script>

<template>
  
  <div class="countdown-timer">
    <time>
      {{formating()}}
    </time>
  </div>

  <div class="countdown-controll">
    <button @click="startStop" class="btn start-stop-btn" :class="isStarted?'started':'stopped'">{{isStarted?"Stop":"Start"}}</button>
    <button @click="reset" class="btn reset-btn">Reset</button>
  </div>

</template>

<style scoped>
  .countdown-timer time {
    font-size: 5rem;
  }

 
  .btn{
    width: 60px;
    height: 60px;
    margin: 8px;
    border-radius: 50%;
    outline: none;
    border: none;
    background-color: var(--color-background-mute);
    color: var(--vt-c-white-mute);
    cursor: pointer;
  }

  .btn:hover{
    opacity: 0.8;
  }

  .started{
    background-color: rgba(128, 0, 0, 0.274);
  }
  .stopped{
    background-color: rgba(0, 128, 0, 0.274); 
  }

</style>