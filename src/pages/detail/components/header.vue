<!-- html -->
<template>
    <div>
        <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
            <i class="iconfont header-abs-back">&#xe624;</i>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
                <i class="iconfont header-fixed-back">&#xe624;</i>
            </router-link>
            景点详情
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .header-abs
        z-index 2
        position absolute
        left 0.2rem
        top 0.2rem
        width 0.8rem
        height 0.8rem
        line-height 0.8rem
        text-align center
        border-radius 50%
        background-color rgba(0, 0, 0, 0.8)
        .header-abs-back
            color #fff
            font-size 0.4rem
    .header-fixed
        z-index 2
        height $headerHeight
        line-height $headerHeight
        overflow hidden
        text-align center
        color #fff
        background-color $bgColor
        font-size 0.32rem
        position fixed
        top 0rem
        left 0rem
        right 0rem
        .header-fixed-back
            width 0.64rem
            text-align center
            font-size 0.4rem
            position absolute
            top 0rem
            left 0rem
            color #fff

</style>

<!-- js -->
<script>
    export default {
        name: "detailHeader",
        data (){
            return{
                showAbs: true,
                opacityStyle: {
                    opacity: 0
                }
            }
        },
        methods: {
            handleScroll (){
                let top = document.documentElement.scrollTop
                if(top >60){
                    let opacity = top / 140
                    opacity = opacity > 1? 1:opacity
                    this.opacityStyle = {
                        opacity
                    }
                    this.showAbs = false
                }else{
                    this.showAbs = true
                }
            }
        },
        activated (){
            window.addEventListener("scroll",this.handleScroll)
        },
        deactivated (){
            window.removeEventListener("scroll",this.handleScroll)
        }
    }
</script>