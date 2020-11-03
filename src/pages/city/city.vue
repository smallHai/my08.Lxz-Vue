<!-- html -->
<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="letterChange"></city-alphabet>
    </div>
</template>

<!-- css -->
<style lang="stylus" scoped>
    
</style>

<!-- js -->
<script>
    import axios from "axios"
    import cityHeader from "./components/header"
    import citySearch from "./components/search"
    import cityList from "./components/list"
    import cityAlphabet from "./components/alphabet"

    export default{
        name: "city",
        data (){
            return{
                cities: {},
                hotCities: [],
                letter: ""
            }
        },
        components: {
            cityHeader,
            citySearch,
            cityList,
            cityAlphabet
        },
        methods: {
            getCityInfo (){
                axios.get('/api/city.json')
                    .then(this.getCityInfoSucc)
                    .catch(this.getCityInfoErr)
            },
            getCityInfoSucc (res){
                res = res.data
                if(res.ret && res.data){
                    let data = res.data
                    this.cities = data.cities
                    this.hotCities = data.hotCities
                }
            },
            getCityInfoErr (err){
                console.log(err);
            },
            letterChange (letter){
                this.letter = letter
            }
        },
        mounted (){
            this.getCityInfo()
        }
    }
</script>