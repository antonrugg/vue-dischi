<template>
  <div id="app">
    <HeaderComponent/>
    <!-- <SelectComponent/> -->
    <MainComponent :url="apiUrl"/>
    <!-- <CardComponent/> -->
  </div>
</template>

<script>


import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
// import SelectComponent from './components/SelectComponent.vue'
// import CardComponent from './components/CardComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
    // SelectComponent
    // CardComponent
  },

  data(){
    return{
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music'
    }
  }


}
</script>

<style lang="scss">
 
@import '@/style/general'; 



</style>
