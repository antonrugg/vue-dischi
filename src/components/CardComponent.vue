<template>
    
        <div class="card d-flex flex-column align-items-center pt-3">
            <img :src="card.poster" :alt="card.genre">
            <p class="title mt-3">{{card.title}}</p>
            <div class="pb-5 d-flex flex-column .justify-content-start">    
                <span class="sub-title">{{card.author}}</span>
                <span class="sub-title">{{card.year}}</span>
            </div>
        </div>
    
</template>

<script>



export default {
    name: 'CardComponent',
    props:{
        card: Object
    }
    
}
</script>

<style lang="scss" scoped>
    @import '@/style/variables';

    .card{
        background-color: $bg-color-nav-and-card;
        

        img{
            width:  70%;
        }

        .title{
            color: white;
            text-transform: uppercase;
        }

        .sub-title{
            color: $color-card-sub-text;
        }
    }

</style>