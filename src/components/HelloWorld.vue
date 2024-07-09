<script setup lang="ts">
defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }} <br> Mi nombre es Victor Aguayo</h1>
    <h3>
      Hola!
      Este es un ejemplo de uso de APIs<br><h4>El lado de front se está usando VUE 3</h4><h4>El Back se está usando Laravel 5.8</h4>
    <h1> <br><a href="https://www.linkedin.com/in/victor-d-aguayo/"> linkedIn</a></h1><br>
    
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
