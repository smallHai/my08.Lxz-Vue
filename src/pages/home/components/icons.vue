<!-- html -->
<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) of pages" :key="index">
                <div class="icon-list" v-for="item of page" :key="item.id">
                    <div class="list-img">
                        <img :src="item.imgUrl">
                    </div>
                    <p class="list-text">{{item.title}}</p>
                </div>
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    
    .icons >>> .swiper-container
        width 100%
        height 0rem
        overflow hidden
        padding-bottom 50%
    .icons
        margin-top 0.2rem
        .icon-list
            width 25%
            height 0rem
            overflow hidden
            float left
            padding-bottom 25%
            position relative
            .list-img
                position absolute
                top 0rem
                left 0rem
                right 0rem
                bottom 0.6rem
                box-sizing border-box
                padding 0.1rem
                display flex
                justify-content center
                align-items center
                >img
                    width 0.9rem
                    height 0.9rem
            .list-text
                height 0.6rem
                line-height 0.6rem
                text-align center
                position absolute
                left 0rem
                right 0rem
                bottom 0rem
                color $darkTextColor
                ellipsis()
            
</style>

<!-- js -->
<script>
    export default{
        name: "homeIcons",
        props: {
            iconList: Array
        },
        data (){
            return{
                swiperOption:{
                    autoplay: 0,
                    pagination: ".swiper-pagination",
                }
            }
        },
        computed: {
            pages (){
                const pages = []
                this.iconList.forEach((item,index)=>{
                    const page = Math.floor(index / 8);
                    if (!pages[page]){
                        pages[page] = [];
                    }
                    pages[page].push(item);
                })
                return pages;
            }
        }
    }
</script>