<template>
  <select @change="showLabelValue($event)">
      <option value="all">All</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="metal">Metal</option>
      <option value="jazz">Jazz</option>
  </select>
</template>

<script>
export default {
    name: 'SelectComponent',
    data(){
        return{
            selectedLabel: ''
        }
    },
    methods: {
        showLabelValue(event){
            this.selectedLabel = event.target.value;
            this.$emit('searchByGenres', this.selectedLabel);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>