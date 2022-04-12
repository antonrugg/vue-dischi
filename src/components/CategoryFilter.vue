<template>
  <select v-model="selectedCategory" @change="changeCategory">
      <option value="">All categories</option>
      <option v-for="category in categories" :key="category" :value="category">
          {{category}}
      </option>
  </select>
</template>

<script>
export default {
    name: 'CategoryFilter',
    props:{
        categories: Array
    },
    data(){
        return {
            selectedCategory: ''
        }
    },
    methods:{
        changeCategory(){
            console.log(this.selectedCategory);
            this.$emit('changedCategory', this.selectedCategory);
        }
    }
}
</script>

<style>

</style>