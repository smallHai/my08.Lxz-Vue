<!-- html -->
<template>
    <transition>
        <slot></slot>
    </transition>
</template>

<!-- css -->
<style lang="stylus" scoped>
    @import "~@/assets/styles/varibles.styl"
    .v-enter,.v-leave-to
        opacity 0
    .v-enter-active,.v-leave-active
        transition opacity 0.5s
</style>

<!-- js -->
<script>
    export default{
        name: "commonAnimation",
        data (){
            return{
                
            }
        }
    }
</script>