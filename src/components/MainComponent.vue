<template>
  <div class="container mt-5">

    <div v-if="cards.length > 0" class="row d-flex gy-5 gx-4 justify-content-between">
         <CardComponent  class="col-12 col-md-6 col-xl-2 " 
         v-for="(card, index) in cards" 
         :key="index" 
         :card="card"/>
    </div>
     
  </div>
</template>

<script>

import axios from 'axios';
import CardComponent from '@/components/CardComponent.vue'

export default {
    name: 'MainComponent',
     data(){
      return{
        cards: []
      }
    },
    props: {
        url: String
    },
    components: {
      CardComponent
    },
    mounted(){
        this.loadData();
    },

    methods: {
        loadData(){
            axios.get(this.url)
            .then((response) => {
                    // console.log(response.data.response)
                    // console.log(response.data.response[0].poster);
                    // console.log(response.data.response[0].title);
                    // console.log(response.data.response[0].author);
                    // console.log(response.data.response[0].year);
                    this.cards = response.data.response;
                    console.log(this.cards[0]);

            })
            .catch(
                  (error) =>{
                    console.log(error);
            })
        }
    }
}
</script>

<style lang="scss" scoped>

</style>