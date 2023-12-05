<template>
    <div class="main-nav container mt-3 p-4 text-center">
        <router-link :to="{name: 'home'}">Pruduct</router-link>
        <router-link :to="{name:'AddProduct'}">Add New Pruduct</router-link>
    </div>
</template>

<script>
export default {

}
</script>

<style>
.main-nav a{
    text-decoration: none;
    padding: 13px;
    color: rgb(27, 31, 27);
}
a.router-link-active{
    border-bottom: 2px solid rgb(55, 222, 18);
}
</style>