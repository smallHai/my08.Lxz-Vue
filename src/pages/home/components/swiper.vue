<!-- html -->
<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <!-- slides -->
            <swiper-slide v-for="itme of swiperList" :key="itme.id">
                <img class="img-swiper" :src="itme.imgUrl">
            </swiper-slide>
            <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .wrapper >>> .swiper-pagination-bullet-active
        background-color #fff
    .wrapper
        width 100%
        height 0rem
        overflow hidden
        background-color #eee
        padding-bottom 56.2%
        .img-swiper
            width 100%
</style>

<!-- js -->
<script>
    export default {
        name: "homeSwiper",
        props: {
            swiperList: Array
        },
        data (){
            return {
                swiperOption: {
                    pagination: ".swiper-pagination",
                    loop: true
                }
            }
        },
        computed: {
            showSwiper(){
                return this.swiperList.length
            }
        }
    }
</script>