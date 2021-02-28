<template>
   <div class="yy-checkbox-group">
        <slot></slot>
    </div>
</template>

<script>
export default {
  name: "yyCheckboxGroup",
  props:{
      value:{
          type:Array
      }
  },
  provide(){
      return {
          CheckboxGroup:this
      }
  }
};
</script>

<style></style>
