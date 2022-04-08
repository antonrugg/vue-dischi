<template>
  <div class="container-fluid d-flex flex-start p-3">
      <img class="img-fluid" src="@/assets/spotify-logo.png" alt="logo spotify">
  </div>
</template>

<script>
export default {
    name: 'HeaderComponent',
    props: { 
        
    }
}
</script>

<style lang="scss" scoped>
    @import '@/style/variables';

    .container-fluid{
        background-color: $bg-color-nav-and-card;

        img{
            min-width: 5%;
            width: 35px;
        }
    }
    
</style>