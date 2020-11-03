<!-- html -->
<template>
    <div>
        <div class="banner" @click="bannerClick">
            <img class="banner-img" :src="bannerImg">
            <div class="banner-info">
                <div class="info-title">{{sightName}}</div>
                <div class="info-number">
                    <i class="iconfont banner-icon">&#xe692;</i>&nbsp;
                    {{num}}
                </div>
            </div>
        </div>
        <common-animation>
            <common-gallary 
                :imgs="gallaryImgs" 
                v-show="showGallary" 
                @close="gallaryClose"
            ></common-gallary>
        </common-animation>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    .banner
        height 0rem
        overflow hidden
        padding-bottom 55%
        position relative
        .banner-img
             width 100%
        .banner-info
            position absolute
            left 0rem
            right 0rem
            bottom 0rem
            line-height 0.6rem
            color #fff
            display flex
            background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
            .info-title
                flex 1
                font-size 0.32rem
                padding 0 0.2rem
            .info-number
                height 0.32rem
                line-height 0.32rem
                margin-top 0.14rem
                padding 0 0.4rem
                border-radius 0.2rem
                background-color rgba(0,0,0,0.7)
                font-size 0.24rem
                .banner-icon
                    font-size 0.24rem
</style>

<!-- js -->
<script>
    import commonGallary from "common/gallary/gallary"
    import commonAnimation from "common/animation/animation"
    export default{
        name: "detailBanner",
        props: {
            sightName: String,
            bannerImg: String,
            gallaryImgs: Array
        },
        components: {
            commonGallary,
            commonAnimation
        },
        data (){
            return{
                showGallary: false
            }
        },
        computed: {
            num (){
                return this.gallaryImgs.length
            }
        },
        methods: {
            bannerClick (){
                this.showGallary = true
            },
            gallaryClose (){
                this.showGallary = false
            }
        }
    }
</script>