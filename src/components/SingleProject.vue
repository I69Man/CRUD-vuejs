<template>
 <div class="product container p-4" :class="{complete: product.change}">
    <div class="action d-flex justify-content-between">
        <h3 @click="showBody = !showBody">{{ product.email }} , {{ product.id }}</h3>
        <div class="icons">
            <i class="bi bi-check2-square" @click="changeComplete"></i>
            <RouterLink :to="{name: 'EditProduct' , params:{id: product.id}}">
               <i class="bi bi-pencil"  @click="newAdd" ></i>
            </RouterLink>
            <i class="bi bi-trash" @click="deleteProduct"></i>
        </div>
    </div>
    <div v-if="showBody" class="details">
        <p>{{ product.body }}</p>
    </div>
 </div>
</template>

<script>
import axios from 'axios'

export default {
  props: ['product'],
  data(){
    return {
        showBody: false,
        url: 'http://localhost:3000/product/',
        
    }
  },
  methods:{
    deleteProduct(){
      axios.delete(this.url + this.product.id)
      .catch(err => {
            console.log(err);
        })
        .finally(() => this.$emit('delete', this.product.id))

      //   fetch(this.url, {method: 'DELETE'})
      //     .then(() => this.$emit('delete', this.product.id))
      //     .catch(err => console.log(err.messege))
    },
  async changeComplete() {
       
    await  axios
       .patch(this.url + this.product.id,{change: !this.product.change})
       .then(() => this.$emit('complete', this.product.id)) 
       .catch(err => console.log(err.message))     
    },
    newAdd() {
      this.$router.push({path:'/add' })
    }
  }
}
</script>

<style>
 .product{
    margin: 20px auto;
    background: white;
    padding: 10px 20px;
    border-radius: 4px;
    box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
    border-left: 4px solid #e90074;
 }
 h3{
    cursor: pointer;
 }
 .bi{
    font-size: 24px;
    margin-left: 16px;
    color: rgb(187, 187, 187)f1f;
    cursor: pointer;
 }
 .bi:hover{
    color: #777;
 }
 .complete {
    border-left: 4px solid #00e969;
 }
</style>