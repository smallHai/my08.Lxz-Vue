<!-- html -->
<template>
    <div>
        <div class="title">周末游玩</div>
        <ul>
            <li class="item border-bottom" v-for="item of weekendList" :key="item.id">
                <div class="item-img">
                    <img :src="item.imgUrl">
                </div>
                <div class="item-info">
                    <p class="info-title">{{item.title}}</p>
                    <p class="info-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    
    .title
        line-height 0.8rem
        background-color #eee
        text-indent 0.2rem
    .item
        width 100%
        .item-img
            height 0rem
            padding-bottom 37%
            overflow hidden
            >img
                width 100%
                overflow hidden
        .item-info
            padding 0.1rem
            .info-title
                line-height 0.54rem
                font-size 0.32rem
                ellipsis()
            .info-desc
                line-height 0.4rem
                color #999
                ellipsis()
</style>

<!-- js -->
<script>
    export default{
        name: "homeWeekend",
        props: {
            weekendList: Array
        },
        data (){
            return{
                
            }
        }
    }
</script>