<template>
  <div id="app">
    <HeaderComponent :logo="'logo'"/>
    <MainComponent/>
    <CardComponent/>
  </div>
</template>

<script>


import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
import CardComponent from './components/CardComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
    CardComponent
  }
}
</script>

<style lang="scss">
 
@import '@/style/general'; 



</style>
