<!-- html -->
<template>
    <ul class="list">
        <li
            class="item"
            v-for="item of letters" 
            :key="item" 
            :ref="item" 
            @click="letterClick" 
            @touchstart.prevent="handleTouchStart" 
            @touchmove="handleTouchMove" 
            @touchend="handleTouchEnd"
        >
            {{item}}
        </li>
    </ul>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .list
        width 0.4rem
        position absolute
        top 1.58rem
        right 0rem
        bottom 0rem
        display flex
        flex-direction column
        justify-content center
        .item
            text-align center
            line-height 0.4rem
            color $bgColor
</style>

<!-- js -->
<script>
    export default{
        name: "cityAlphabet",
        data (){
            return{
                touchStatus: false,
                timer: null
            }
        },
        props: {
            cities: Object
        },
        computed: {
            letters (){
                let letters = []
                for(let i in this.cities) {
                    letters.push(i)
                }
                return letters
            }
        },
        methods: {
            letterClick (e){
                this.$emit("change",e.target.innerText)
            },
            handleTouchStart (){
                this.touchStatus = true
            },
            handleTouchMove (e){
                if(this.touchStatus){
                    if(this.timer){ 
                        clearTimeout(this.timer)
                    }
                    this.timer = setTimeout(()=>{
                        let startY = this.$refs["A"][0].offsetTop
                        let touchY = e.touches[0].clientY -79
                        let index = Math.floor((touchY - startY) / 20)
                        if(index>=0 && index<this.letters.length){
                            this.$emit("change",this.letters[index])
                        }
                    },16);
                }
            },
            handleTouchEnd (){
                this.touchStatus = false
            }
        }
    }
</script>