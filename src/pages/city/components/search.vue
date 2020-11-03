<!-- html -->
<template>
    <div>
        <div class="search">
            <input class="search-input" v-model="keyword" type="text" placeholder="输入城市名或拼音">
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul>
                <li 
                    class="search-item border-bottom" 
                    v-for="item of list" 
                    :key="item.id"
                    @click="cityClick(item.name)"
                >
                    {{item.name}}
                </li>
                <li class="search-item border-bottom" v-show="hasNoData">
                    没有找到匹配数据
                </li>
            </ul>
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .search
        height 0.72rem
        padding 0 0.1rem
        background-color $bgColor
        .search-input
            width 100%
            height 0.62rem
            line-height 0.62rem
            text-align center
            border-radius 0.06rem
            color #666
            padding 0 0.1rem
            box-sizing border-box
    .search-content
        z-index 1
        overflow hidden
        position absolute
        top 1.58rem
        left 0rem
        right 0rem
        bottom 0rem
        background-color #eee
        .search-item
            line-height 0.62rem
            padding-left 0.2rem
            color #666
            background-color #fff
</style>

<!-- js -->
<script>
    import { mapMutations } from "vuex"
    import BScroll from 'better-scroll'
    export default{
        name: "citySearch",
        props: {
            cities: Object
        },
        data (){
            return{
                keyword:"",
                list: [],
                timer: null,
            }
        },
        computed: {
            hasNoData (){
                return !this.list.length
            }
        },
        methods: {
            cityClick (city){
                this.changeCity(city)
                this.$router.push("/")
            },
            ...mapMutations(["changeCity"])
        },
        watch: {
            keyword (){
                if(!this.keyword){
                    this.list = []
                    return
                }
                if(this.timer){
                    clearTimeout(this.timer)
                }
                this.timer = setTimeout(()=>{
                    let result = []
                    for(let i in this.cities){
                        this.cities[i].forEach((value)=>{
                            if(value.spell.indexOf(this.keyword)>-1 ||
                                value.name.indexOf(this.keyword)>-1){
                                result.push(value)
                            }
                        })
                    }
                    this.list = result
                },100)
            }
        },
        mounted (){
            this.scroll = new BScroll(this.$refs.search)
        }
    }
</script>