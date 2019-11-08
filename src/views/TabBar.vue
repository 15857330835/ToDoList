<template>
    <nav class="bar bar-tab">
        <a class="tab-item external" href="#" v-for="tabbar in tabbars" :key="tabbar.id" :class="[type==tabbar.text&&'active']" @click="changeType(tabbar.text)">
            {{ tabbar.text }}
        </a>
  </nav>
</template>

<script>
export default {
    props:['type'],
    data(){
        return{
            tabbars:[
                {
                    id:1,
                    text:'A'
                },
                {
                    id:2,
                    text:'F'
                },
                {
                    id:3,
                    text:'U'
                }
            ]
        }
    },
    methods:{
        changeType(val){
            this.$emit('change_type',val)
        }
    }
}
</script>