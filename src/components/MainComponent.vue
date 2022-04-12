<template>
  <div class="container mt-5">
    <div class="row mb-5">
      <!--CategoryFilter @changedCategory="performCategoryFilter" :categories="genres" />

      <AuthorFilter @changedAuthor="performAuthorFilter" :authors="authors" /-->

        <GenericFilter :label="'All Categories'" @changedOption="performCategoryFilter" :options="genres" />

        <GenericFilter :label="'All Author'" @changedOption="performAuthorFilter" :options="authors" />
    </div>
    <div class="row">
      <RecordItem v-for="(record, index) in filteredRecords" :key="index" :record="record" />
    </div>  
  </div>
</template>

<script>

import axios from 'axios';

import RecordItem from '@/components/RecordItem.vue'

//import CategoryFilter from '@/components/CategoryFilter.vue'
//import AuthorFilter from '@/components/AuthorFilter.vue'

// !!!! invece che utilizzare 2 componenti diversi pressoché uguali
// (cambiano solo i nomi delle props/data e la label per la prima option)
// usiamo un componente generico (nomi props/data etc generici + prop per passare la label prima option )
import GenericFilter from '@/components/GenericFilter.vue'

export default {
    name: 'MainComponent',
    props: {
      url: String
    },
    data(){
      return {
        records: [],
        selectedCategory: '',
        selectedAuthor: ''
      }
    },
    computed:{

      authors(){
        const authors = this.records
                .map((record)=>record.author);

        const uniqueAuthors = [...new Set(authors)]; // trick per eliminare elementi duplicati

        return uniqueAuthors;
      },

      genres(){
        /*
        // 
        const uniqueGenres = [];
        this.records.forEach((item)=>{
          if (!uniqueGenres.includes(item.genre)){
            uniqueGenres.push(item.genre);
          }
        })
        */


        const genres = this.records
                        .map((record)=>record.genre);

        const uniqueGenres = [...new Set(genres)]; // trick per eliminare elementi duplicati

        return uniqueGenres;
      },

      filteredRecords(){
          /*
          // vecchia versione in cui verifichiamo una sola condizione
          if (this.selectedCategory===''){
                return this.records;
              }
          */

        /*
        // associo l'array intero oppure filtrato per categoria in base al valore della select html
        const filteredByCategory = this.selectedCategory===''
              ? this.records
              : this.records.filter(({genre}) => genre === this.selectedCategory);

              return (this.selectedAuthor !== '')
                 ? filteredByCategory.filter(({author})=> author === this.selectedAuthor)
                 : filteredByCategory

        */
        let filteredByCategory = this.records;
        if (this.selectedCategory!==''){
              filteredByCategory = filteredByCategory.filter(({genre}) => genre === this.selectedCategory);
        }

        if (this.selectedAuthor !== ''){
                filteredByCategory = filteredByCategory.filter(({author})=> author === this.selectedAuthor);
        }
        return filteredByCategory
      }

    },
    created(){
      axios.get(this.url).then(({ data, status })=>{
        console.log(status, data);
        if (status===200 && data.success){
          this.records = data.response;
         // console.log(this.records[0]);
        }
      }).catch((error)=>{
        console.log(error);
      });
    },
    methods: {
      performCategoryFilter(selectedCategory){
          console.log('MainComponent selectedCategory', selectedCategory);
          this.selectedCategory = selectedCategory;
      },
      performAuthorFilter(selectedAuthor){
         this.selectedAuthor = selectedAuthor;
      }
    },
    components: {
      RecordItem,
      // CategoryFilter,
      // AuthorFilter,
      GenericFilter     
    }
}
</script>

<style lang="scss" scoped>


  .row > * {
    width: 20%;
    padding: 0.5rem;
  }
</style>