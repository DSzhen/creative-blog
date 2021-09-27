<template>
  <header class="header-content">
    <el-menu :default-active="activeIndex"
             class="el-menu-demo"
             mode="horizontal"
             @select="handleSelect"
             background-color="#fff"
             text-color="#000"
             active-text-color="#ffd04b">
      <div class="user-title">XX的个人博客 |<span> ❤爱的人正在路上❤</span></div>
      <el-menu-item index="/mian">博客首页</el-menu-item>
      <el-menu-item index="/personal/notes">个人笔记</el-menu-item>
      <el-submenu index="/technology">
        <template slot="title">技术杂谈</template>
        <el-menu-item index="/technology/vueSpecial">vue</el-menu-item>
        <el-menu-item index="/technology/nodejsSpecial">nodejs</el-menu-item>
        <el-menu-item index="/technology/pythonSpecial">Python</el-menu-item>
      </el-submenu>
      <el-menu-item index="/aboutMe">关于我</el-menu-item>
      <el-menu-item index="/leaveWord">留言</el-menu-item>
      <div class="user-login"><a href="">登录</a>/<a href="">注册</a></div>
    </el-menu>
  </header>
</template>

<script>
export default {
  data() {
    return {
      activeIndex: "/mian"
    };
  },
  created() { },
  methods: {
    handleSelect(key, keyPath) {
      console.log("切换标签页");
    }
  },
  mounted() { },
  watch: {}
};
</script>

<style lang="less" scoped>
.header-content {
  width: 100%;
  .user-title {
    margin-right: 100px;
    height: 60px;
    line-height: 60px;
    color: #000;
    font-size: 22px;
    font-weight: bold;
    span {
      font-size: 15px;
      color: cadetblue;
    }
  }
  .user-login {
    margin-left: 240px;
    height: 60px;
    line-height: 60px;
    color: #000;
    font-size: 13px;
    font-weight: bold;
    a {
      color: #000;
    }
  }
  .el-menu--horizontal .el-menu--popup-bottom-start {
    margin-top: 0px;
  }
  ul {
    width: 100%;
    list-style-type: none;
    padding: 0px;
    margin: 0px;
  }
  ul.el-menu-demo.el-menu--horizontal.el-menu {
    display: flex;
    justify-content: center;
  }
}
</style>