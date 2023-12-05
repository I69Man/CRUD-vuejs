<template>
    <form class="bg-secondary p-4 mt-5 container" @submit.prevent="handleEdit">
  <div class="mb-3 container mt-5">
    <label for="exampleFormControlInput1" class="form-label text-white">Email address</label>
    <input type="email" class="form-control" v-model="email" id="exampleFormControlInput1" placeholder="name@example.com" required>
  </div>
  <div class="mb-3 container">
    <label for="exampleFormControlTextarea1" class="form-label text-white">Body textarea</label>
    <textarea class="form-control" id="exampleFormControlTextarea1" rows="3" v-model="body"></textarea>
    <div class="col-auto text-center">
    <button type="submit" class="btn btn-success mb-3 mt-4">Edit Product</button>
  </div>
  </div>
</form>
</template>

<script>
import axios from 'axios'
export default {
    props: ['id'],
data(){
    return {
        email:'',
        body:""
    }
},
mounted() {
    axios.get('http://localhost:3000/product/' + this.id)
        .then((res) => {
            this.email = res.data.email
            this.body = res.data.body
        })
        .catch((err) => console.log(err.message))
       
},
methods: {
   
    handleEdit(){
        axios.patch('http://localhost:3000/product/' + this.id, {email: this.email,body: this.body})
        .catch(err => err.message)
        .finally(this.$router.push('/'))
    }
}
}
</script>

<style>

</style>