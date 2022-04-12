<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent :url="apiUrl" />
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from '@/components/MainComponent.vue'


export default {
  name: 'App',
  data() {
    return {
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music'
    }
  },
  components: {
    HeaderComponent,
    MainComponent
  }
}
</script>

<style lang="scss">
  @import '@/style/common';
</style>
