<template>
  <div class="org-tree">
    <el-input placeholder="输入关键字进行过滤"
              v-model="filterText"
              clearable>
    </el-input>
    <el-tree :data="treeData"
             :props="defaultProps"
             default-expand-all
             empty-text="数据加载中"
             node-key="id"
             :filter-node-method="filterNode"
             ref="tree"
             :default-expanded-keys="arrExpanded"
             :expand-on-click-node="true"
             @node-click="handleNodeClick">
      <span class="tree-node"
            slot-scope="{ data }"
            :title="data.name">
        <span class="tree-title">{{ data.name }}</span>
      </span>
    </el-tree>
  </div>
</template>
<script>
export default {
  name: "OrgTree",
  data() {
    return {
      filterText: "",
      treeData: [],
      arrExpanded: [],
      defaultProps: {
        children: "children",
        label: "name"
      },
      projectObj: {}
    }
  },
  watch: {
    filterText(val) {
      this.$refs.tree.filter(val)
    }
  },
  mounted() {
    this.getTreeData()
  },
  methods: {
    // 获取组织数据
    getTreeData() {
      this.treeData = [{ "children": [{ "children": [{ "name": "深圳二期", "tenantId": 5600196, "id": 5606424, "type": "BIDAREA", "parentId": 5605112 }, { "name": "新劳务手提", "tenantId": 5600196, "id": 5606428, "type": "BIDAREA", "parentId": 5605112 }, { "name": "实测实量", "tenantId": 5600196, "id": 5607408, "type": "BIDAREA", "parentId": 5605112 }, { "name": "斑马测试标段", "tenantId": 5600196, "id": 5610815, "type": "BIDAREA", "parentId": 5605112 }, { "name": "万达二期斑马计划", "tenantId": 5600196, "id": 5610858, "type": "BIDAREA", "parentId": 5605112 }, { "name": "0412", "tenantId": 5600196, "id": 5612268, "type": "BIDAREA", "parentId": 5605112 }, { "name": "715", "tenantId": 5600196, "id": 5612295, "type": "BIDAREA", "parentId": 5605112 }, { "name": "0909", "tenantId": 5600196, "id": 5614442, "type": "BIDAREA", "parentId": 5605112 }], "name": "工程监管930分期工程监管930项目", "tenantId": 5600196, "id": 5605112, "type": "PARK", "parentId": 5605111 }, { "children": [{ "children": [{ "children": [], "name": "工程一部门", "tenantId": 5600196, "id": 5611506, "type": "ORG", "parentId": 5607296 }], "name": "工程管理部", "tenantId": 5600196, "id": 5607296, "type": "ORG", "parentId": 5605241 }], "name": "天津赫海建筑有限公司天津赫海建筑有限公司天津赫海建筑有限公司天津赫海建筑有限公司天津赫海建筑有限公司天津赫海建筑有限公司天津赫海建筑有限公司", "tenantId": 5600196, "id": 5605241, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "部门A", "tenantId": 5600196, "id": 5606612, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "设计", "tenantId": 5600196, "id": 5606797, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "测试组织", "tenantId": 5600196, "id": 5606809, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "劳务分公司", "tenantId": 5600196, "id": 5606832, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "测试人员的组织", "tenantId": 5600196, "id": 5606943, "type": "ORG", "parentId": 5605111 }, { "children": [{ "name": "市政二期", "tenantId": 5600196, "id": 5607256, "type": "BIDAREA", "parentId": 5607254 }, { "name": "0330项目", "tenantId": 5600196, "id": 5607265, "type": "BIDAREA", "parentId": 5607254 }], "name": "视频测试", "tenantId": 5600196, "id": 5607254, "type": "PARK", "parentId": 5605111 }, { "children": [], "name": "上海分公司", "tenantId": 5600196, "id": 5607274, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "云筑劳务公司", "tenantId": 5600196, "id": 5607516, "type": "ORG", "parentId": 5605111 }, { "children": [{ "name": "标段二", "tenantId": 5600196, "id": 5607941, "type": "BIDAREA", "parentId": 5607937 }], "name": "020202yx", "tenantId": 5600196, "id": 5607937, "type": "PARK", "parentId": 5605111 }, { "children": [], "name": "0305云筑", "tenantId": 5600196, "id": 5608063, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "030502云筑", "tenantId": 5600196, "id": 5608066, "type": "ORG", "parentId": 5605111 }, { "children": [], "name": "斑马测试", "tenantId": 5600196, "bidAreaName": "北京万达一期", "id": "5608120", "type": "PARK", "parentId": 5605111, "parkId": "5608118" }, { "children": [{ "name": "颐和园一期", "tenantId": 5600196, "id": 5609445, "type": "BIDAREA", "parentId": 5609172 }], "name": "施工页面嵌入", "tenantId": 5600196, "id": 5609172, "type": "PARK", "parentId": 5605111 }, { "children": [{ "name": "颐和园1期", "tenantId": 5600196, "id": 5609413, "type": "BIDAREA", "parentId": 5609353 }, { "name": "可删", "tenantId": 5600196, "id": 5611155, "type": "BIDAREA", "parentId": 5609353 }], "name": "页面嵌入测试", "tenantId": 5600196, "id": 5609353, "type": "PARK", "parentId": 5605111 }, { "children": [{ "children": [], "name": "419-远程巡检测试-分期名称", "tenantId": 5600196, "bidAreaName": "标段1", "id": "5610937", "type": "PARK", "parentId": 5610882, "parkId": "5610935" }, { "children": [{ "name": "标段一", "tenantId": 5600196, "id": 5611999, "type": "BIDAREA", "parentId": 5610996 }, { "name": "标段二", "tenantId": 5600196, "id": 5612382, "type": "BIDAREA", "parentId": 5610996 }], "name": "419-远程巡检项目2-分期名称", "tenantId": 5600196, "id": 5610996, "type": "PARK", "parentId": 5610882 }, { "children": [{ "name": "标段三", "tenantId": 5600196, "id": 5611995, "type": "BIDAREA", "parentId": 5611989 }, { "name": "标段四", "tenantId": 5600196, "id": 5611997, "type": "BIDAREA", "parentId": 5611989 }], "name": "624-项目进度可视化-多标段", "tenantId": 5600196, "id": 5611989, "type": "PARK", "parentId": 5610882 }, { "children": [{ "name": "625-质安2标段", "tenantId": 5600196, "id": 5612450, "type": "BIDAREA", "parentId": 5612007 }], "name": "625-质量安全大屏测试", "tenantId": 5600196, "id": 5612007, "type": "PARK", "parentId": 5610882 }, { "children": [{ "name": "国投进度简报", "tenantId": 5600196, "id": 5612272, "type": "BIDAREA", "parentId": 5612270 }, { "name": "标段3", "tenantId": 5600196, "id": 5612446, "type": "BIDAREA", "parentId": 5612270 }], "name": "713-测试项目", "tenantId": 5600196, "id": 5612270, "type": "PARK", "parentId": 5610882 }, { "children": [{ "name": "标段2", "tenantId": 5600196, "id": 5614682, "type": "BIDAREA", "parentId": 5614678 }], "name": "913003执法记录仪左树显示3", "tenantId": 5600196, "id": 5614678, "type": "PARK", "parentId": 5610882 }, { "children": [], "name": "913004执法记录仪左树显示4", "tenantId": 5600196, "bidAreaName": "标段1", "id": "5614688", "type": "PARK", "parentId": 5610882, "parkId": "5614686" }, { "children": [{ "name": "标段2", "tenantId": 5600196, "id": 5614694, "type": "BIDAREA", "parentId": 5614690 }, { "name": "标段3", "tenantId": 5600196, "id": 5614696, "type": "BIDAREA", "parentId": 5614690 }, { "name": "标段4", "tenantId": 5600196, "id": 5614698, "type": "BIDAREA", "parentId": 5614690 }, { "name": "标段5", "tenantId": 5600196, "id": 5614700, "type": "BIDAREA", "parentId": 5614690 }], "name": "913005执法记录仪左树显示5", "tenantId": 5600196, "id": 5614690, "type": "PARK", "parentId": 5610882 }], "name": "京沪分公司", "tenantId": 5600196, "id": 5610882, "type": "ORG", "parentId": 5605111 }, { "children": [{ "children": [{ "children": [{ "children": [{ "name": "421-标段-1", "tenantId": 5600196, "id": 5611170, "type": "BIDAREA", "parentId": 5611168 }, { "name": "33", "tenantId": 5600196, "id": 5615852, "type": "BIDAREA", "parentId": 5611168 }], "name": "421-新建项目-远程巡检-分期名称", "tenantId": 5600196, "id": 5611168, "type": "PARK", "parentId": 5611167 }], "name": "项目管理部", "tenantId": 5600196, "id": 5611167, "type": "ORG", "parentId": 5611166 }], "name": "山东分公司", "tenantId": 5600196, "id": 5611166, "type": "ORG", "parentId": 5611165 }], "name": "华北区", "tenantId": 5600196, "id": 5611165, "type": "ORG", "parentId": 5605111 }, { "children": [{ "name": "AI预警测试", "tenantId": 5600196, "id": 5611479, "type": "BIDAREA", "parentId": 5611175 }], "name": "项目级人管理测试(勿删）", "tenantId": 5600196, "id": 5611175, "type": "PARK", "parentId": 5605111 }, { "children": [{ "name": "设备A加设备B", "tenantId": 5600196, "id": 5611241, "type": "BIDAREA", "parentId": 5611233 }, { "name": "设备加视频", "tenantId": 5600196, "id": 5611243, "type": "BIDAREA", "parentId": 5611233 }], "name": "0427授权文件测试", "tenantId": 5600196, "id": 5611233, "type": "PARK", "parentId": 5605111 }, { "children": [], "name": "060201计划预警", "tenantId": 5600196, "bidAreaName": "1", "id": "5611705", "type": "PARK", "parentId": 5605111, "parkId": "5611703" }, { "children": [{ "name": "0616一标段", "tenantId": 5600196, "id": 5611899, "type": "BIDAREA", "parentId": 5611897 }], "name": "0616计划预警（勿删）", "tenantId": 5600196, "id": 5611897, "type": "PARK", "parentId": 5605111 }, { "children": [{ "name": "1", "tenantId": 5600196, "id": 5612078, "type": "BIDAREA", "parentId": 5612076 }, { "name": "2", "tenantId": 5600196, "id": 5612412, "type": "BIDAREA", "parentId": 5612076 }], "name": "0628进度", "tenantId": 5600196, "id": 5612076, "type": "PARK", "parentId": 5605111 }, { "children": [], "name": "0816计划", "tenantId": 5600196, "bidAreaName": "1", "id": "5612735", "type": "PARK", "parentId": 5605111, "parkId": "5612733" }, { "children": [], "name": "授权文件有视频，配置无", "tenantId": 5600196, "bidAreaName": "授权文件有视频，配置无", "id": "5612850", "type": "PARK", "parentId": 5605111, "parkId": "5612848" }], "name": "工程监管930", "tenantId": 5600196, "id": 5605111, "type": "ORG", "parentId": null }, { "children": [], "name": "组织级0305云筑（勿删）", "tenantId": 5600196, "id": 5608073, "type": "ORG", "parentId": null }, { "children": [], "name": "云筑劳务测试公司", "tenantId": 5600196, "id": 5608107, "type": "ORG", "parentId": null }]
    },
    filterNode(value, data) {
      if (!value) return true
      return data.name.indexOf(value) !== -1
    },
  }
}
</script>
<style lang="less" scoped>
.org-tree {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
</style>
