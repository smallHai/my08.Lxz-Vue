<!-- html -->
<template>
    <div>
        <home-header></home-header>
        <home-swiper :swiperList="swiperList"></home-swiper>
        <home-icons :iconList="iconList"></home-icons>
        <home-recommend :recommendList="recommendList"></home-recommend>
        <home-weekend :weekendList="weekendList"></home-weekend>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    
</style>

<!-- js -->
<script>
    import axios from "axios"
    import { mapState } from "vuex"
    import homeHeader from "./components/header"
    import homeSwiper from "./components/swiper"
    import homeIcons from "./components/icons"
    import homeRecommend from "./components/recommend"
    import homeWeekend from "./components/weekend"
    export default{
        name: "home",
        data (){
            return{
                lastCity: "",
                swiperList: [],
                iconList: [],
                recommendList: [],
                weekendList: []
            }
        },
        components: {
            homeHeader,
            homeSwiper,
            homeIcons,
            homeRecommend,
            homeWeekend
        },
        computed: {
            ...mapState(["city"])
        },
        methods: {
            getHomeInfo (){
                axios.get('/api/index.json?city='+this.city)
                    .then(this.getHomeInfoSucc)
                    .catch(this.getHomeInfoErr)
            },
            getHomeInfoSucc (res){
                res = res.data
                if(res.ret && res.data){
                    let data = res.data
                    this.swiperList = data.swiperList
                    this.iconList = data.iconList
                    this.recommendList = data.recommendList
                    this.weekendList = data.weekendList
                }
            },
            getHomeInfoErr (err){
                console.log(err);
            }
        },
        mounted (){
            this.lastCity = this.city
            this.getHomeInfo()
        },
        activated (){
            if(this.lastCity !== this.city){
                this.lastCity = this.city
                this.getHomeInfo()
            }
        }
    }
</script>