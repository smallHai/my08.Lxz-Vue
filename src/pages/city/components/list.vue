<!-- html -->
<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{currentCity}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div 
                        class="button-wrapper"
                        v-for="item of hotCities"
                        :key="item.id"
                        @click="cityClick(item.name)"
                    >
                        <div class="button">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <ul class="item-list">
                    <li 
                        class="item border-bottom" 
                        v-for="innerItem of item" 
                        :key="innerItem.id"
                        @click="cityClick(innerItem.name)"
                    >
                        {{innerItem.name}}
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .border-topbottom
        &:before
            border-color #ccc
        &:after
            border-color #ccc
    .border-bottom
        &:before
            border-color #ccc
    .list
        position absolute
        top 1.58rem
        left 0rem
        right 0rem
        bottom 0rem
        overflow hidden
        .title
            line-height 0.54rem
            background-color #eee
            padding-left 0.2rem
            color #666
            font-size 0.26rem
        .button-list
            padding 0.1rem 0.6rem 0.1rem 0.1rem
            overflow hidden
            .button-wrapper
                width 33.33%
                float left
            .button
                margin 0.1rem
                text-align center
                padding 0.1rem 0rem
                border 0.02rem solid #ccc
                border-radius 0.06rem
        .item-list
            .item
                line-height 0.76rem
                padding-left 0.2rem
</style>

<!-- js -->
<script>
    import { mapState,mapMutations } from "vuex"
    import BScroll from 'better-scroll'
    export default{
        name: "cityList",
        props: {
            cities: Object,
            hotCities: Array,
            letter: String
        },
        data (){
            return{
                
            }
        },
        computed: {
            ...mapState({
                currentCity: "city"
            })
        },
        methods: {
            cityClick (city){
                this.changeCity(city)
                this.$router.push("/")
            },
            ...mapMutations(["changeCity"])
        },
        mounted (){
            this.scroll = new BScroll(this.$refs.wrapper)
        },
        watch: {
            letter (){
                if(this.letter){
                    let element = this.$refs[this.letter][0]
                    this.scroll.scrollToElement(element)
                }
            }
        }
    }
</script>