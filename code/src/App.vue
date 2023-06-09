<template>
  <div id="app" class="app">
    <HeaderTransport />
    <BestTransport/> 
    
  </div>
</template>

<script>
import HeaderTransport from './components/HeaderTransport.vue'
import BestTransport from './components/BestTransport.vue'


export default {
  name: 'App',
  components: {
    HeaderTransport,
    BestTransport,
    

  }
}
</script>

<style>
 .app{
  background-color: gray;
  height: 100vh;
 }
</style>
