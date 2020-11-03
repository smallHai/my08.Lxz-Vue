<!-- html -->
<template>
    <div>
        <div class="item" v-for="(item,index) of categoryList" :key="index">
            <div class="item-title border-bottom">
                <span class="title-icon"></span>
                {{item.title}}
            </div>
            <div v-if="item.children" class="item-chlidren">
                <detail-list :categoryList="item.children"></detail-list>
            </div>
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .item-title
        line-height 0.8rem
        font-size 0.32rem
        padding 0 0.2rem
        .title-icon
            width 0.36rem
            height 0.36rem
            display inline-block
            margin-right 0.1rem
            background url('/static/images/icons/d_list.png') 0rem -0.45rem no-repeat
            background-size 0.4rem 3rem
            position relative
            top 0.06rem
            left 0.06rem
    .item-chlidren
        padding 0 0.4rem
</style>

<!-- js -->
<script>
    export default{
        name: "detailList",
        props: {
            categoryList: Array
        },
        data (){
            return{
                
            }
        }
    }
</script>