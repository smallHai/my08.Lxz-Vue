<!-- html -->
<template>
    <div>
        <div class="title">热销推荐</div>
        <ul>
            <router-link 
                tag="li" 
                class="item border-bottom" 
                v-for="item of recommendList" 
                :key="item.id" 
                :to="'/detail/'+item.id" 
            >
                <img class="item-img" :src="item.imgUrl">
                <div class="item-info">
                    <p class="info-title">{{item.title}}</p>
                    <p class="info-desc">{{item.desc}}</p>
                    <button class="info-btn">查看详情</button>
                </div>
            </router-link>
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
        margin-top 0.2rem
    .item
        display flex
        height 1.9rem
        overflow hidden
        .item-img
            width 1.7rem
            height 1.7rem
            padding 0.1rem
        .item-info
            flex 1
            padding 0.1rem
            min-width 0rem
            .info-title
                line-height 0.54rem
                font-size 0.32rem
                ellipsis()
            .info-desc
                line-height 0.4rem
                color #999
                ellipsis()
            .info-btn
                line-height 0.44rem
                background-color #ff9300
                padding 0 0.2rem
                border-radius 0.06rem
                margin-top 0.16rem
                color #fff;
</style>

<!-- js -->
<script>
    export default{
        name: "homeRecommend",
        props: {
            recommendList: Array
        },
        data (){
            return{
                
            }
        }
    }
</script>