<template>
  <div class=ac-card>
    <div class="card">
       <img :src="record.poster" :alt="record.title" />
       <h2> {{record.title}} </h2>
       <div>{{record.author}} </div>
       <div>{{record.year}} </div>
    </div>
  </div>
</template>

<script>
/*
author: (…)
genre: (…)
poster: (…)
title: (…)
year: (…)

*/

export default {
    name: 'RecordItem',
    props: {
        record: Object
    }
}
</script>

<style lang="scss" scoped>
    .ac-card{
        padding: 0.5rem;
        .card{
            background-color: #2e3a46;
            text-align: center; 
            padding: 1rem;
            min-height: 350px;
            h2 {
                font-size: 20px;
                color: white;
                text-transform: uppercase;
                margin-top: 0.5rem;
            }
        }     
    }
</style>