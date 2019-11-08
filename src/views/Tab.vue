<template>
    <header class="bar bar-nav">
        <a class="icon icon-left pull-left"></a>
        <a class="icon icon-edit pull-right" @click="changeInutFlag"></a>
        <h1 class="title">todolist</h1>
    </header>
</template>


<script>
export default {
    methods:{
        changeInutFlag(){
            this.$emit('change_input_flag')
        }
    }
}
</script>