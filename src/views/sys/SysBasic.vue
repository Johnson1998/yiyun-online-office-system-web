<template>
  <el-tabs v-model="activeName" type="card" >
    <el-tab-pane label="部门管理" name="DepMana"><DepMana></DepMana></el-tab-pane>
    <el-tab-pane label="职位管理" name="PostMana"><PostMana></PostMana></el-tab-pane>
    <el-tab-pane label="职称管理" name="JoblevelMana"><JoblevelMana></JoblevelMana></el-tab-pane>
    <el-tab-pane label="奖惩规则" name="EcMana"><EcMana></EcMana></el-tab-pane>
    <el-tab-pane label="权限组" name="PermissMana"><PermissMana></PermissMana></el-tab-pane>
  </el-tabs>
</template>

<script>
import DepMana from "@/components/sys/basic/DepMana";
import EcMana from "@/components/sys/basic/EcMana";
import JoblevelMana from "@/components/sys/basic/JoblevelMana";
import PermissMana from "@/components/sys/basic/PermissMana";
import PostMana from "@/components/sys/basic/PostMana";

export default {
    name: "SysBasic",
    data(){
      return{
        activeName: "PermissMana"
      }
    },
  components:{
      DepMana,
      EcMana,
      JoblevelMana,
      PermissMana,
      PostMana,
  }
}
</script>

<style>

</style>