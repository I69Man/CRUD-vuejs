<template>
  <div class="container text-white p-2">
    <h1 class="text-center bg-secondary rounded p-4">Data By jsonplaceholder</h1>

  </div>
  <div class="home">
    <FilterNav class="container" @filterChange="current = $event" :current="current"/>
    <div v-if="products.length">
      <div v-for="product in filteredProjects" :key="product.id">
        <SingleProject :product="product" @delete="handleDelete" @complete="handleComplete"/>
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject.vue'
import FilterNav from '../components/FilterNav.vue'
import axios from "axios";

export default {
  name: 'HomeView',
  components: {SingleProject , FilterNav},
  data() {
    return {
      products: [],
      showBody: false,
      current: 'all'
    }
  },
  mounted() {
    axios.get('http://localhost:3000/product')
      .then((response) => {
        this.products = response.data
      }).catch(err => console.log(err.message))
  },
  methods: {
    handleDelete(id) {
      this.products = this.products.filter(item => {
        return item.id !== id
      })
    },
    handleComplete(id) {
      let p = this.products.find(item => {
        return item.id === id
      })
      p.change = !p.change
    }
  },
  computed: {
    filteredProjects(){
      if(this.current === 'completed'){
        return this.products.filter(item => item.change)
      }
      else if(this.current === 'ongoing'){
        return this.products.filter(item => !item.change)
      
      }
      else{
        return this.products
      }
    }
  }
 
}
</script>
