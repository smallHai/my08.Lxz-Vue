<!-- html -->
<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <i class="iconfont icon-back">&#xe624;</i>
        </router-link>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    
    .header
        height $headerHeight
        line-height $headerHeight
        overflow hidden
        text-align center
        color #fff
        background-color $bgColor
        font-size 0.32rem
        position relative
        .icon-back
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
    export default{
        name: "cityHeader",
        data (){
            return{
                
            }
        }
    }
</script>