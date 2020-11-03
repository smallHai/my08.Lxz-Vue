<!-- html -->
<template>
    <div>
        <detail-header></detail-header>
        <detail-banner 
            :sightName="sightName" 
            :bannerImg="bannerImg"
            :gallaryImgs="gallaryImgs" 
        ></detail-banner>
        <div class="content">
            <detail-list :categoryList="categoryList"></detail-list>
        </div>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    .content
        height 20rem
</style>

<!-- js -->
<script>
    import axios from "axios"
    import detailHeader from "./components/header"
    import detailBanner from "./components/banner"
    import detailList from "./components/list"
    export default{
        name: "detail",
        data (){
            return{
                sightName: "",
                bannerImg: "",
                gallaryImgs: [],
                categoryList: []
            }
        },
        components: {
            detailHeader,
            detailBanner,
            detailList,
        },
        methods: {
            getDetailInfo (){
                axios.get("/api/detail.json",{
                    params:{
                        id: this.$route.params.id
                    }
                })
                .then(this.getDetailInfoSucc)
                .catch(this.getDetailInfoErr)
            },
            getDetailInfoSucc (res){
                res = res.data
                if(res.ret && res.data){
                    let data = res.data
                    this.sightName = data.sightName
                    this.bannerImg = data.bannerImg
                    this.gallaryImgs = data.gallaryImgs
                    this.categoryList = data.categoryList
                }
            },
            getDetailInfoErr (err){
                console.log(err);
            }
        },
        mounted (){
            this.getDetailInfo()
        }
    }
</script>