<template>
  <el-container>
    <el-container :style="{'height':mainHeight+'px'}">
      <el-aside style="width: 18%" id="doc_main">
        <img src="../assets/img/logo.png" width="100%" style="margin-top: 25px">
        <el-col>
          <el-menu
              text-color="#797979"
              active-text-color="#ffd04b"
              :router="true"
              :default-active="defaultActive"
          >
            <!-- 使用 vue-router 的模式，启用该模式会在激活导航时以 index 作为 path 进行路由跳转 -->
            <!-- 当前激活的菜单选项是当前的路径，保证刷新的时候激活样式不掉 -->
            <el-menu-item  index="/doctor/patient">
              <div class="menuCenter">
                <i class="el-icon-s-custom"></i>
                <span slot="title">我的病人</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/cottoms">
              <div class="menuCenter">
                <i class="el-icon-s-order"></i>
                <span slot="title">电子病例</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/hospitalization">
              <div class="menuCenter">
                <i class="el-icon-s-ticket"></i>
                <span slot="title">住院管理</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/report">
              <div class="menuCenter">
                <i class="el-icon-document"></i>
                <span slot="title">报告查询</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/discharge">
              <div class="menuCenter">
                <i class="el-icon-document"></i>
                <span slot="title">出院管理</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/recipe">
              <div class="menuCenter">
                <i class="el-icon-edit-outline"></i>
                <span slot="title">处方管理</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/counsel">
              <div class="menuCenter">
                <i class="el-icon-question"></i>
                <span slot="title">就诊咨询</span>
              </div>
            </el-menu-item>
            <el-menu-item index="/doctor/personal">
              <div class="menuCenter">
                <i class="el-icon-user-solid"></i>
                <span slot="title">个人信息</span>
              </div>
            </el-menu-item>
          </el-menu>
        </el-col>
        <!-- 定义医生功能模块左侧菜单部分 -->
      </el-aside>
      <el-main style="background-color:rgb(241,243,244)">
        <el-col class="content">
          <!-- <div> -->
          <router-view></router-view>
          <!-- </div> -->
        </el-col>
        <!-- 右侧展示内容，根据菜单的点击进行路由跳转 -->
      </el-main>
    </el-container>
    <el-footer style="box-shadow:0px 0px 10px 10px rgb(240, 240, 240);height: 60px">
      <span>
      <el-avatar
          src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
      ></el-avatar>
      <em>张医生</em>
      </span>
      <el-button icon="el-icon-switch-button" round style="float: right;margin-top: 0.8%">退出登陆</el-button>
    </el-footer>
    <!-- 定义页面尾部的退出登录部分 -->
  </el-container>
</template>
<script>
export default {
  data() {
    return {
      logoHeight: 20,
      mainHeight: window.innerHeight * 0.92,
      // footerHeight: window.innerHeight * 0.08
    };
  },
  mounted() {
    var windowHeight = window.innerHeight;
    console.log();
  },
  methods: {
    // exitLogin() {
    //   this.$http("/shiro/logout", "post").then((res) => {
    //     //  console.log(res)
    //     if (res.msg == "ok") {
    //       this.$store.commit("setLogin", false);
    //       //把本地存储里的login变为false
    //       this.$router.push({path: "/login"});
    //       //  退出登录成功后跳转到登录页面
    //     }
    //   });
    // },
    //  退出登录方法
  },
  computed: {
    defaultActive() {
      //   // console.log(this.$route.path.split("/"));
      //   let pathArr = this.$route.path.split("/");
      //   let activePath = "/" + pathArr[1] + "/" + pathArr[2];
      //   return activePath;
    },
    //控制element-ui navmenu组件的default-active属性，因为这里有子路由，所以如果只是简单的定义 :default-active="$route.path",那么在子路由状态下如果刷新的话就会丢失激活的状态，我们使用一个计算属性 保证在子路由状态下刷新也有激活状态
  },
};
</script>
<style lang="scss" scoped>
.content {
  padding: 35px 50px;
  box-sizing: border-box;
  height: 100%;
}

span {
  font-size: 16px //菜单栏字号

}

#doc_bot {
  height: 60px;
  width: 100%;

  .exit {
    background-color: #30c0e0;
    display: flex;
    float: right;
    justify-content: center;
    align-items: center;
    //margin-top: 10px;

    em {
      margin-left: 17px;
    }
  }

  .setup {
    display: flex;
    justify-content: space-evenly;
    margin-top: 10px;
  }

  .el-icon-s-custom {
    padding-left: 40px;
  }
}

.menuCenter {
  //background-color: red;
  padding-left: 25%;
}

</style>
<style lang="scss">
.el-menu-item:hover{
  background-color: rgb(238,238,238) !important;
}

.el-menu-item.is-active {
  color: black !important;
}
</style>
