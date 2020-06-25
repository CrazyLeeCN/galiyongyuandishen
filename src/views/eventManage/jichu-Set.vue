<template>
  <div class="tab-container">
    <el-tabs v-model="activeName" style="margin-top:15px;" type="border-card">
      <el-tab-pane v-for="item in tabMapOptions" :key="item.key" :label="item.label">
        <component :is="item.component" />
      </el-tab-pane>
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
    tabpane: TabPane,
    tabpane2: TabPane2,
    tabpane3: TabPane3,
    tabpane4: TabPane4,
    tabpane5: TabPane5,
    tabpane6: TabPane6
  },
  data() {
    return {
      tabMapOptions: [
        { label: '基础设置', key: 'CN', component: TabPane },
        { label: '摊位设置', key: 'US', component: TabPane2 },
        { label: '宝箱奖励', key: 'CN1', component: TabPane3 },
        { label: '每日任务', key: 'CN2', component: TabPane4 },
        { label: '宠物奖励', key: 'CN3', component: TabPane5 },
        { label: '事件位置', key: 'CN4', component: TabPane6 }
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
