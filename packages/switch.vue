<template>
 <div class="yy-switch" @click="handleClick" :class="{'is-checked':value}">
        <!-- name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据。 -->
        <input ref="input" type="checkbox" class="yy-switch_input" :name="name">
        <span class="yy-switch_core" ref="core">
            <span class="yy-switch_button"></span>
        </span>
    </div>
</template>

<script>
export default {
name: "yySwitch",
props:{
    value:{
        type:Boolean,
        default:false
    },
    activeColor:{
        type:String,
        default:""
    },
    inactiveColor:{
        type:String,
        default:""
    },
    name:{
        type:String,
        default:""
    }
},
methods:{
      async handleClick(){
        this.$emit('input',!this.value)
       await this.$nextTick()
            this.setColor()  
            this.$refs.input.checked = this.value 
    },
    setColor(){
          //修改开关颜色
    if(this.activeColor || this.inactiveColor){
        let color = this.value ? this.activeColor : this.inactiveColor
        this.$refs.core.style.borderColor = color
        this.$refs.core.style.backgroundColor = color
    }
    }
},
mounted(){
  this.setColor()
   this.$refs.input.checked = this.value 
}
}
</script>

<style lang="scss">
 .yy-switch{
    display: inline-block;
    align-items: center;
    position: relative;
    font-size: 14px;
    line-height: 20px;
    vertical-align: middle;
    .yy-switch_core{
    margin: 0;
    display: inline-block;
    position: relative;
    width: 40px;
    height: 20px;
    border: 1px solid #dcdfe6;
    outline: none;
    border-radius: 10px;
    box-sizing: border-box;
    background: #dcdfe6;
    cursor: pointer;
    transition: border-color .3s,background-color .3s;
    vertical-align: middle;
    .yy-switch_button{
      position:absolute;
      top: 1px;
      left: 1px;
      border-radius: 100%;
      transition: all .3s;
      width: 16px;
      height: 16px;
      background-color: #fff;
      }
    }
  }
  // 选中样式
  .is-checked {
    .yy-switch_core{
      border-color: #409eff;
      background-color: #409eff;
      .yy-switch_button {
        transform: translateX(20px);
      }
    }
  }
  // 隐藏input标签
  .yy-switch_input{
    position:absolute;
    width: 0;
    height: 0;
    opacity: 0;
    margin: 0;
  }
</style>