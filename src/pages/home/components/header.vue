<!-- html -->
<template>
    <div class="header">
        <div class="header-left">
            <i class="iconfont icon-back">&#xe624;</i>
        </div>
        <div class="header-input">
            <i class="iconfont icon-search">&#xe632;</i>
            输入城市/景点/游玩/主题
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{city}}
                <i class="iconfont icon-arrow">&#xe64a;</i>
            </div>
        </router-link>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    
    .header
        display flex
        height $headerHeight
        line-height $headerHeight
        background-color $bgColor
        color #fff
        .header-left
            width 0.64rem
            float left 
            .icon-back
                display block
                text-align center
                line-height 0.86rem
                font-size 0.4rem
        .header-input
            height 0.64rem
            line-height 0.64rem
            margin 0.12rem 0 0.12rem 0.2rem
            flex 1
            background-color #fff
            border-radius 0.1rem
            color #ccc
            padding-left 0.2rem
        .header-right
            min-width 1.04rem
            padding 0 0.1rem
            float right
            text-align center
            color #fff
            .icon-arrow
                font-size 0.24rem

</style>

<!-- js -->
<script>
    import { mapState } from "vuex"
    export default {
        name: "homeHeader",
        computed: {
            ...mapState(["city"])
        }
    }
</script>