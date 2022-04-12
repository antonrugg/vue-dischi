<template>
  <select v-model="selectedAuthor" @change="changeAuthor">
      <option value="">All authors</option>
      <option v-for="author in authors" :key="author" :value="author">
          {{author}}
      </option>
  </select>
</template>

<script>
export default {
    name: 'AuthorFilter',
    props:{
        authors: Array
    },
    data(){
        return {
            selectedAuthor: ''
        }
    },
    methods:{
        changeAuthor(){
            console.log(this.selectedAuthor);
            this.$emit('changedAuthor', this.selectedAuthor);
        }
    }
}
</script>

<style>

</style>