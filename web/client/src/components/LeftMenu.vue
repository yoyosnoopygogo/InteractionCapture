<template>
    <el-row class="menu_page">
      
      <el-col :span="14">
        <el-menu
          active-text-color="#409eff"
          background-color="#324057"
          class="el-menu-vertical-demo"
          text-color="#fff">
            <router-link to="/home">
                <el-menu-item index="0">
                    <template #title>
                        <i class="fa fa-margin fa-server"></i>
                        <span slot="title">首页</span>
                    </template>
                </el-menu-item>
                <template v-for="item in items">
                    <el-sub-menu v-if="item.children" :index="item.path" :key="item.path">
                        <template  #title>
                            <i :class="'fa fa-margin '+item.icon"></i>
                            <span slot="title">{{item.name}}</span>
                        </template>
                        <router-link v-for="(citem,cindex) in item.children" :to="citem.path"
                        :key="cindex">
                            <el-menu-item index="citem.path">
                                <span slot="title">{{citem.name}}</span>
                            </el-menu-item>
                        </router-link>
                    </el-sub-menu>
                </template>
            </router-link>
        </el-menu>
      </el-col>
    </el-row>
</template>









<script>
    export default{
      name:'left-menu',
    
  data() {
    return {
      items: [
        {
          icon: "fa-money",
          name: "任务管理",
          path: "fund",
          children: [{ path: "tasklist", name: "任务列表" }]
        },
        {
          icon: "fa-asterisk",
          name: "信息管理",
          path: "info",
          children: [{ path: "infoshow", name: "个人信息" }]
        }
      ]
    };

    }
}
  </script>

<style scoped>
.menu_page {
  position: fixed;
  top: 71px;
  left: 0;
  min-height: 100%;
  background-color: #324057;
  z-index: 99;
}
.el-menu {
  border: none;
}
.fa-margin {
  margin-right: 5px;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 180px;
  min-height: 400px;
}
.el-menu-vertical-demo {
  width: 35px;
}
.el-sub-menu .el-menu-item {
  min-width: 120px;
}

.hiddenDropdown,
.hiddenDropname {
  display: none;
}
a {
  text-decoration: none;
}
</style>