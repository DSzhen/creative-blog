<template>
  <div class="main">
    <Header class="microBlog-Header"></Header>
    <div class="microBlog-content">
      <div class="left-tree">
        <microTree></microTree>
      </div>
      <div class="right-content">
        <div>
          <p>JAVA快速入门</p>
          <p>阅读：<span>564564564</span></p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Header from "@/components/microHeader.vue";
import microTree from "@/components/microTree.vue";
export default {
  name: "microBlog",
  components: {
    Header,
    microTree
  },
  data() {
    return {

    }
  },
  mounted() {
  },
  methods: {}
}
</script>
<style lang="less" scoped>
.main {
  height: 100%;
  width: 100%;
  position: relative;
  overflow: hidden;
  .microBlog-Header {
    ul {
      background-color: #fff !important;
    }
  }
  .microBlog-content {
    height: calc(100% - 65px);
    width: 100%;
    display: flex;
    .left-tree {
      width: 20%;
      height: 100%;
      overflow: auto;
      background: #fff;
    }
    .right-content {
      width: 79%;
      height: 100%;
      overflow: auto;
      background: #fff;
      padding: 11px;
    }
  }
}
</style>