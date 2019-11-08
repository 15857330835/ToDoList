<template>
  <div id="app">
    <div class="page-group">
      <div class="page page-current">
        <Tab @change_input_flag='changeInputFlag'></Tab>
        <Container :todos='newtodos' @change_flag='changeFlag' @check='check' :input_flag='input_flag' @add='addItem' @change_input_flag='changeInputFlag'></Container>
        <MyMask :mask_flag='mask_flag' @close_mask='cloceMask' @remove='remove' :active_index='active_index'></MyMask>
        <TabBar :type='type' @change_type='changeType'></TabBar>
      </div>
    </div>
  </div>
</template>

<script>
import Tab from './views/Tab'
import Container from './views/Container'
import MyMask from './views/MyMask'
import TabBar from './views/TabBar'
export default {
  name: 'app',
  components: {
    Tab,
    Container,
    MyMask,
    TabBar
  },
  data(){
    return{
      mask_flag:false,
      active_index:0,
      input_flag:false,
      type:'A',
      todos:[
        {
          id:1,
          task:'任务一',
          done:false
        },
        {
          id:2,
          task:'任务二',
          done:false
        },
        {
          id:3,
          task:'任务三',
          done:false
        }
      ]
    }   
  },
  methods:{
    changeFlag(index){
      this.todos[index].done=!this.todos[index].done
    },
    check(index){
      var flag = this.todos[index].done
      if(flag){
        this.remove(index)
      }else{
        this.active_index=index
        this.mask_flag=true
      }
    },
    remove(index){
      this.todos.splice(index,1)
    },
    cloceMask(){
      this.mask_flag=false
    },
    changeInputFlag(){
      this.input_flag=!this.input_flag
    },
    addItem(val){
      this.todos.unshift({
        id:sort(this.todos)[0].id+1,
        task:val,
        done:false
      })
    },
    changeType(val){
      this.type=val
    }
  },
  computed:{
    newtodos(){
      switch (this.type) {
        case 'F':
          return this.todos.filter(item=>item.done)
          break;
        case 'U':
          return this.todos.filter(item=>!item.done)
          break;
      
        default:
          return this.todos
          break;
      }
    }
  }
}

function sort(arr){
  return arr.sort((a,b)=>{
    return b.id-a.id
  })
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  color #2c3e50
  margin-top 60px
</style>
