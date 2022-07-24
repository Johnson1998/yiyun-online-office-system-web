<template>
  <div>
    <div class = 'permissManaTool'>
      <el-input size="small" aria-placeholder="请输入角色英文名" v-model="role.name">
        <template slot="prepend">ROLE_</template>
      </el-input>
      <el-input size="small" aria-placeholder="请输入角色中文名" v-model="role.nameZh">
      </el-input>
      <el-button size="small" type="primary" icon="el-icon-plus">添加角色</el-button>
    </div>
    <div class="permissManaMain">
      <el-collapse accordion @change="change">
        <el-collapse-item :title="r.nameZh" :name="r.id" v-for="(r, index) in roles" :key="index">
          <el-card class="box-card">
            <div slot="header" class="clearfix">
              <span>可访问资源</span>
              <el-button style="float: right; padding: 3px 0;color: red" type="text" icon="el-icon-delete"></el-button>
            </div>
            <div>
              <el-tree
                  show-checkbox
                  :data="allMenus"
                  :props="defaultProps"></el-tree>
            </div>
          </el-card>
        </el-collapse-item>
      </el-collapse>
    </div>
  </div>
</template>

<script>
export default {
  name: "PermissMana",
  data() {
    return {
      role: {
        name: '',
        nameZh: ''
      },
      roles: [],
      allMenus:[],
      defaultProps: {
        children: 'children',
        label:'name',
      }
    }
  },
  mounted() {
    this.initRoles()
  },
    methods:{
    change(rid){
      if (rid) {
        this.initAllMenus()
      }
      },
    initAllMenus() {
      this.getRequest('/system/basic/permiss/menus').then(resp=>{
        if (resp) {
          this.allMenus = resp;
        }
      })
      },
    initRoles(){
      this.getRequest('/system/basic/permiss/').then(resp=>{
        if (resp) {
          this.roles = resp;

        }
      })
    }
  }
}
</script>

<style scoped>
  .permissManaTool{
    display: flex;
    justify-content: flex-start;
  }
  .permissManaTool .el-input {
    width: 300px;
    margin-right: 3px;
  }
  .permissManaMain {
    margin-top: 10px;
    width: 700px;
  }
</style>