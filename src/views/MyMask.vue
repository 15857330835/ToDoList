<template>
    <div class="mask-box" v-if="mask_flag">
        <div class="mask-bg" @click="closeMask"></div>
        <div class="mask-content">
            <p>你确定要删除吗？</p>
            <button class="button button-danger button-fill pull-right" @click="remove(active_index)">确定</button>
        </div>
    </div>
</template>

<script>
export default {
    props:['mask_flag','active_index'],
    methods:{
        closeMask(){
            this.$emit('close_mask')
        },
        remove(index){
            this.closeMask()
            this.$emit('remove',index)
        }
    }
}
</script>

<style lang="stylus" scoped>
.mask-box
    position fixed
    top 0
    left 0
    width 100%
    height 100%
    z-index 100
    .mask-bg
        position absolute
        top 0
        left 0
        width 100%
        height 100%
        background black
        opacity .5
    .mask-content
        position: absolute
        left 0
        right 0
        top: 0
        bottom 0
        margin auto
        width 80%
        height 110px
        background white
        border-radius 10px
        padding 10px
        overflow hidden
        p
            font-weight bold
        button
            width 80px
            height 30px
            font-size 14px
</style>