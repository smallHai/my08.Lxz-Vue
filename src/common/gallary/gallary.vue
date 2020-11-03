<!-- html -->
<template>
    <div class="container" @click="gallaryClick">
        <div class="wrapper">
            <swiper :options="swiperOption">
                <swiper-slide v-for="(item,index) of imgs" :key="index">
                    <img class="img-swiper" :src="item">
                </swiper-slide>
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .container >>> .swiper-container
        overflow inherit
    .container
        display flex
        flex-direction column
        justify-content center
        position fixed
        left 0rem
        right 0rem
        top 0rem
        bottom 0rem
        z-index 99
        background-color #000;
        .wrapper
            width 100%
            height 0rem
            padding-bottom 100%
            .img-swiper
                width 100%
            .swiper-pagination
                color #fff
                bottom -1rem
</style>

<!-- js -->
<script>
    export default{
        name: "commonGallary",
        props: {
            imgs: {
                type: Array,
                default (){
                    return []
                }
            }
        },
        data (){
            return{
                swiperOption: {
                    pagination: ".swiper-pagination",
                    paginationType: "fraction",
                    observeParents: true,
                    observer: true
                }
            }
        },
        methods: {
            gallaryClick(){
                this.$emit("close")
            }
        }
    }
</script>