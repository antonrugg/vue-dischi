<template>
  <div class="container-sm mt-5 pb-5">

    <div><SelectComponent/></div>

    <div v-if="cards.length > 0" class="row d-flex gy-5 gx-4 justify-content-between">
         <CardComponent  class="col-12 col-md-6 col-xl-2 " 
         v-for="item in filteredList" 
         :key="item.index" 
         :card="item"/>
    </div>
     
  </div>
</template>

<script>

import axios from 'axios';
import CardComponent from '@/components/CardComponent.vue';
import SelectComponent from '@/components/SelectComponent.vue';

export default {
    name: 'MainComponent',
     data(){
      return{
        cards: [],
        selectedLabel: 'all'
      }
    },
    props: {
        url: String
    },
    computed: {
      filteredList(){
        if(this.selectedLabel === 'all'){
          return this.cards;
        }

        const filtered = this.cards.filter(item =>{
          return item.genre.toLowerCase().includes(this.genre.toLowerCase());
        });

        return filtered.filter((item) => item.genre.toLowerCase().includes(this.selectedLabel.toLowerCase()));
      }
    },
    components: {
      CardComponent,
      SelectComponent,
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