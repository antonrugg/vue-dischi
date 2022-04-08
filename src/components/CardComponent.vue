<template>
    <main class="col-12 col-md-3 col-sm-4">
        <div class="card d-flex flex-column">
            <img src="https://picsum.photos/300/200" alt="card image test">
            <p class="title">title</p>
            <p class="sub-title">sub-title</p>
        </div>
    </main>
</template>

<script>
export default {
    name: 'CardComponent',
}
</script>

<style lang="scss" scoped>
    @import '@/style/variables';

    .card{
        background-color: $bg-color-nav-and-card;
        .title{
            color: white;
        }

        .sub-title{
            color: $color-card-sub-text;
        }
    }

</style>