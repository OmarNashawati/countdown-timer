<script setup>
  import Timer from './components/Timer.vue';

</script>

<template>


  <header>
    <h1>Countdown Timer</h1>
  </header>

  <main>
    <Timer />
  </main>
 
</template>

<style scoped>

header{
  padding: 1rem;
  text-align: center;
  font-size: 25px;
}

main{
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

</style>
