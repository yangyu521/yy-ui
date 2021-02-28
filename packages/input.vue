<template>
<div class="yy-input" :class="{'yy-input_suffix' : showSuffix}">
  <input  class="yy-input_inner"
         :class="{'is-disabled' : disabled }"
         :placeholder="placeholder"
          :name="name"
         :disabled=disabled
         :value="value"
          :type="showPassword ? (passwordVisible ? 'text' : 'password') : type"
         @input="handleInput">
          <span class="yy-input_suffix" v-if="showSuffix">
            <i class="yy-icon yy-icon-quxiao" v-if="clearable && value" @click="clear"></i>
            <i class="yy-icon yy-icon-yanjing" v-if="showPassword" @click="handlePassword"
               :class="passwordVisible ? 'yy-icon-yanjing-active' : ''"></i>
          </span>
</div>
</template>
<script>
export default {
name: "yyInput",
  props:{
      placeholder:{
        type:String,
        default:""
      },
    type:{
        type:String,
        default: ''
    },
    name:{
        type:String,
        default:""
    },
    disabled:{
        type:Boolean,
        default:false
    },
    value:{
        type:String,
        default:""
    },
    clearable:{
        type:Boolean,
        default:false
    },
    showPassword:{
        type:Boolean,
        default:false
    }
  },
  data(){
      return{
        passwordVisible:false
      }
  },
  computed:{
    showSuffix(){
      return this.clearable || this.showPassword
    }
  },
  methods:{
            handleInput(e){
              this.$emit('input',e.target.value)
            },
            clear(){
              this.$emit('input','')
            },
             handlePassword(){
                   this.passwordVisible = !this.passwordVisible
            }
  }
}
</script>
<style lang="scss">
.yy-input{
  width: 30;
  position: relative;
  font-size: 14px;
  display: inline-block;
.yy-input_inner{
  -webkit-appearance: none;
  background-color: #fff;
  background-image: none;
  border: 1px solid #dcdfe6;
  border-radius: 4px;
  box-sizing: border-box;
  color: black;
  display: inline-block;
  font-size: inherit;
  height: 40px;
  line-height: 40px;
  outline: none;
  padding: 0 15px;
  transition: border-color .2s cubic-bezier(.645,045,.355,1);
  width: 100%;

&:focus{
   outline: none;
   border-color: #22d1f0;
 }
// input禁用样式
      &.is-disabled{
     background-color: #f5f7fa;
     border-color: #e4e7ed;
     color: #c0c4cc;
     cursor:not-allowed;
   }
}
}
// 后面加suffix的意思是后面如果有后缀的话，触发该样式
   .yy-input_suffix{
.yy-input_inner{
  padding-right: 30px;
}
.yy-input_suffix{
  position: absolute;
  right: 10px;
  height: 100%;
  top: 0;
  line-height: 40px;
  text-align: center;
  color: #c0c4cc;
  transition: all .3s;
  z-index: 900;
  .yy-icon-yanjing-active{
    color: #66b1ff;
  }
i{
  color: #c0c4cc;
  font-size: 14px;
  cursor: pointer;
  transition: color .2s cubic-bezier(.645,.045,.355,1);
}
}
}
</style>