<template>
  <!--   <yy-input placeholder="请输入用户名" type="password" name="username" v-model="username"></yy-input>-->
    <!--   <yy-input type="text" v-model="username" clearable></yy-input>-->
    <!--   <yy-input type="password" show-password v-model="aa"></yy-input>-->
    <!--   <yy-input v-model="username" clearable></yy-input>-->
    <!-- <yy-switch v-model="active"></yy-switch>
    <yy-switch v-model="aa" active-color="green" inactive-color="red" name="username"></yy-switch>
    <yy-radio label="0" v-model="gender">男</yy-radio>
      <yy-radio label="1" v-model="gender">女</yy-radio>
       <yy-radio label="2" v-model="gender">保密</yy-radio> -->
    <!-- <yy-radio-group v-model="gender">
      <yy-radio label="0">男</yy-radio>
      <yy-radio label="1">女</yy-radio>
    </yy-radio-group> -->
    <!-- <yy-checkbox v-model="avtive">是否选中</yy-checkbox> -->
    <!-- <yy-checkbox-group v-model="hobby">
      <yy-checkbox label="抽烟"></yy-checkbox>
      <yy-checkbox label="喝酒"></yy-checkbox>
      <yy-checkbox label="烫头"></yy-checkbox>
    </yy-checkbox-group> -->
    <yy-form :model="model" label-width="150px">
        <yy-form-item label="用户名">
          <yy-input placeholder="请输入用户名" v-model="model.username"></yy-input>
        </yy-form-item>
        <yy-form-item label="选择">
            <yy-switch v-model="model.active"></yy-switch>
        </yy-form-item>
    </yy-form>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      // active: false,
      // aa: false,
      // username: "aaaa",
      // gender: "1",
      // avtive:false,
      hobby:['抽烟','喝酒',"烫头"],
      model:{
        username:"",
        active:true
      }
    };
  },
  methods: {},
};
</script>

<style lang="scss">
// #app{
//   .yy-input{
//     width: 180px;
//   }
// }
</style>
