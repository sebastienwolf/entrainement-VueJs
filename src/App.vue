<script setup>

</script>

<template>
  <div id="app">
 <Home/>
  </div>
  
</template>

<script lang="ts">
// import RestaurantCard from './components/RestaurantCard.vue'
// import RestaurantRow from './components/RestaurantRow.vue';
import Home from './page/home.vue';
export default {
  name: 'App',
  components : {
    Home,
  }
}
</script>

<style scoped>
@import url('style/reset.css');
@import url('https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap');

#app{
  display: block;
  grid-template-columns: unset;
  width: 100vh;
  padding: 20px;

 /* @media only screen and (min-width: 1024px){
    display: block;
  grid-template-columns: unset;
  } */
}

</style>
