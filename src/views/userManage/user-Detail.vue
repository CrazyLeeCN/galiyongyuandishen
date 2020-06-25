<template>
  <div class="tab-container">


    <label class="radio-label" style="padding-left:0;">{{ $t('usermanagetip.tip1') }}</label>
    <label class="radio-label" style="padding-left:200;">{{ $t('usermanagetip.tip1') }}</label>

    <label class="radio-label" style="padding-left:400;">{{ $t('usermanagetip.tip17') }}</label>
    <label class="radio-label" style="padding-left:600;">{{ $t('usermanagetip.tip1') }}</label>
    <br/>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip2') }}</label>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>

    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip18') }}</label>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>
    <br/>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip7') }}</label>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>

    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip3') }}</label>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>
    <br/>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip8') }}</label>
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>

    <el-tabs v-model="activeName" style="margin-top:15px;" type="border-card">
      <el-tab-pane v-for="item in tabMapOptions" :key="item.key" :label="item.label" :name="item.key">
        <keep-alive>
          <tab-pane v-if="activeName==item.key" :type="item.key" @create="showCreatedTimes" />
        </keep-alive>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import TabPane from './components/TabPane'

export default {
  name: 'Tab',
  components: { TabPane },
  data() {
    return {
      tabMapOptions: [
        { label: '游戏记录', key: 'CN' },
        { label: '获得奖励', key: 'US' }
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
