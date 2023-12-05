<template>
    <nav class="filter-nav">
        <button class="border rounded fw-bold"  @click="upfateFilter('all')" :class="{active: current === 'all'}">View All</button>
        <button class="ms-3 border rounded fw-bold" @click="upfateFilter('completed')" :class="{active: current === 'completed'}">Completed</button>
        <button class="ms-3 border rounded fw-bold" @click="upfateFilter('ongoing')" :class="{active: current === 'ongoing'}">Ongoing</button>
    </nav>
</template>

<script>
export default {
    props: ['current'],
   methods: {
    upfateFilter(by){
        this.$emit('filterChange' , by)
    }
   }
}
</script>

<style>
.filter-nav button.active {
    background: rgb(32, 227, 74);
    color: #fff;
    padding: 2px;
}
</style>