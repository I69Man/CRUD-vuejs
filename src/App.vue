<template>
  <Navbar />
  
  <RouterView/>
  
</template>


<script>
import Navbar from './components/Navbar.vue'
export default {
 
  components: { Navbar },
 
  
}

    
</script>

<style>

#app {
  font-family: Vazirmatn, sans-serif;
  color: #2c3e50;
}
</style>
