<template>
    <div class="content">
        <input type="text" name="" id="" v-if="input_flag" @keyup.enter="add">
        <div class="card" v-for='(todo,index) in todos' :key='todo.id'>
            <div class="card-content">
                <div class="card-content-inner">
                    <p> {{ todo.task }} </p> 
                    <div class="btn-box pull-right">
                        <button class="button button-success" :class="{'button-fill':todo.done}" @click='changeFlag(index)'><i class="icon icon-check"></i></button>
                        <button class="button button-danger" @click="check(index)"><i class="icon icon-remove"></i></button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:['todos','input_flag'],
    methods:{
        changeFlag(index){
            this.$emit('change_flag',index)
        },
        check(index){
            this.$emit('check',index)
        },
        changeInutFlag(){
            this.$emit('change_input_flag')
        },
        add(e){
            this.$emit('add',e.target.value)
            this.changeInutFlag()
        }
    }
}
</script>

<style lang="stylus" scoped>
.card-content-inner
    overflow hidden

.btn-box
    display flex
    .button
        margin-right 10px
</style>