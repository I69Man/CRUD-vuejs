<template>
  <!-- <div>{{ getAdd() }}</div>
  <div>{{ bookStore.age }}</div> -->
 
<form class="bg-secondary p-4 mt-5 container" @submit.prevent="handleSubmit">
  <div class="mb-3 container mt-5">
    <label for="exampleFormControlInput1" class="form-label text-white">Email address</label>
    <input type="email" class="form-control" v-model="email" id="exampleFormControlInput1" placeholder="name@example.com" required>
  </div>
  <div class="mb-3 container">
    <label for="exampleFormControlTextarea1" class="form-label text-white">Body textarea</label>
    <textarea class="form-control" id="exampleFormControlTextarea1" rows="3" v-model="body"></textarea>
    <div class="col-auto text-center">
    <button type="submit" @click="sendForm" class="btn btn-success mb-3 mt-4">Add Product</button>
  </div>
  </div>
</form>
</template>

<script>
import axios from 'axios'


export default {
  data() {
    return {
      postId: 2,
      name: 'iman',
      email:'',
      body:'',
      
    }
  },
  methods: {
  
    handleSubmit() {
      const product = {
        postId: this.postId,
       
        email: this.email,
        body: this.body,
        
      }
    
      
        axios.post('http://localhost:3000/product' , product)
        .then(res => this.product = res.data)
        .catch((err) => {
            console.log(err.message);
        })
        this.$router.push('/')
   
    },
  
  },



}
</script>
