<template>
    <div class="yy-form-item">
         <label class="yy-form-item_label" :style=labelStyle>{{label}}</label>
         <div class="yy-form-item_content">
             <slot></slot>
         </div>
     </div>
</template>

<script>
export default {
    name:"yyFormItem",
    props:{
        label:String
    },
    inject:['Form'],
    computed:{
      labelStyle(){
        return {
          width:this.Form.labelWidth
        }
      }
    }
}
</script>

<style lang="scss">
  .yy-form-item{
    margin-bottom: 25px;
    .yy-form-item_label{
      text-align: right;
      vertical-align: middle;
      float: left;
      font-size: 14px;
      color: #606266;
      line-height: 40px;
      padding: 0 12px 0 0;
      box-sizing: border-box;
    }
    .yy-form-item_content{
      line-height: 40px;
      position: relative;
      font-size: 14px;
      overflow: hidden;
      display: inline;
    }
  }
</style>