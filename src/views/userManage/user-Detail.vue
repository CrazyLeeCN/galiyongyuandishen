<template>
  <div class="tab-container" @click="test()">

    <el-row :gutter="20">
      <el-col v-for="item in userMap" :span="12">
        <UserCom :msg="item" />
      </el-col>
    </el-row>

    <!-- <label class="radio-label" style="padding-left:0;">{{ $t('usermanagetip.tip1') }}</label>
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
    <label class="radio-label" style="padding-left:100;">{{ $t('usermanagetip.tip1') }}</label>-->

    <el-tabs v-model="activeName" style="margin-top:15px;" type="border-card">
      <el-tab-pane
        v-for="item in tabMapOptions"
        :key="item.key"
        :label="item.label"
        :name="item.key"
      >
        <keep-alive>
          <tab-pane v-if="activeName==item.key" :type="item.key" @create="showCreatedTimes" />
        </keep-alive>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import TabPane from './components/TabPane'
import UserCom from './components/UserCom'

export default {
  name: 'Tab',
  components: { TabPane, UserCom },
  data() {
    return {
      tabMapOptions: [
        { label: '游戏记录', key: 'CN' },
        { label: '获得奖励', key: 'US' }
      ],
      userMap: [
        { label: '用户名', value: '张三' },
        { label: '上次登录时间', value: '2020-04-28 18:23:15' },
        { label: '手机号', value: '15868126666' },
        { label: '创建时间', value: '2020-04-28 18:23:15' },
        { label: '万里通积分', value: '23465' },
        { label: '状态', value: '正常' },
        { label: '口袋金币', value: '238' }
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
    },
    test() {
      this.$set(this.userMap, 0, { label: '口袋金币', value: '238' })
      console.log(this.userMap)
    }
  }
}
</script>

<style scoped>
.tab-container {
  margin: 30px;
}
.el-col {
  line-height: 40px;
}
.el-row {
  width: 800px;
}
.el-col > span {
  padding-left: 40px;
}
</style>
