<template>
   <div class="yy-radio-group">
          <slot></slot>
      </div>
</template>

<script>
export default {
name:"yyRadioGroup",
provide(){
    return {
        RadioGroup:this
    }
},
props:{
    value:null
},
data(){
    return{
        aa:1,
        bb:2
    }
},
}
</script>

<style>

</style>