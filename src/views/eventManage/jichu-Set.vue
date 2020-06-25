<template>
  <div class="tab-container">

    <el-tabs v-model="activeName" style="margin-top:15px;" type="border-card">
      <el-tab-pane label="基础设置"><tabpane /></el-tab-pane>
      <el-tab-pane label="摊位设置"><tabpane2 /></el-tab-pane>
      <el-tab-pane label="宝箱奖励"><tabpane3 /></el-tab-pane>
      <el-tab-pane label="每日任务"><tabpane4 /></el-tab-pane>
      <el-tab-pane label="宠物奖励"><tabpane5 /></el-tab-pane>
      <el-tab-pane label="事件位置"><tabpane6 /></el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import TabPane from './components/TabPane'
import TabPane2 from './components/TabPane2'
import TabPane3 from './components/TabPane3'
import TabPane4 from './components/TabPane4'
import TabPane5 from './components/TabPane5'
import TabPane6 from './components/TabPane6'

export default {
  name: 'Tab',
  components: { 
    tabpane:TabPane, 
    tabpane2:TabPane2,
    tabpane3:TabPane3,
    tabpane4:TabPane4,
    tabpane5:TabPane5,
    tabpane6:TabPane6
  },
  data() {
    return {
      tabMapOptions: [
        { label: '基础设置', key: 'CN' },
        { label: '摊位设置', key: 'US' },
        { label: '宝箱奖励', key: 'CN1' },
        { label: '每日任务', key: 'CN2' },
        { label: '宠物奖励', key: 'CN3' },
        { label: '事件位置', key: 'CN4' },
      ],
      activeName: 'CN',
      createdTimes: 0
    }
  },
  watch: {
    activeName(val) {
      this.$router.push(`${this.$route.path}?tab=${val}`)
    }
  },
  created() {
    // init the default selected tab
    const tab = this.$route.query.tab
    if (tab) {
      this.activeName = tab
    }
  },
  methods: {
    showCreatedTimes() {
      this.createdTimes = this.createdTimes + 1
    }
  }
}
</script>

<style scoped>
  .tab-container {
    margin: 30px;
  }
</style>
