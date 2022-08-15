<template>
  <el-tabs v-model="activeName" class="demo-tabs">
    <el-tab-pane v-for="item in tabList" :label="item.label" :name="item.key" >
      <component :is="item.key"></component>
    </el-tab-pane>
  </el-tabs>
</template>
<script lang="ts" setup>
  import { ref } from 'vue';

  const tabList = [
    {
      label: '项目捐赠',
      key: 'ProjectDonation'
    },{
      label: '公开信息',
      key: 'PublicInfo'
    },{
      label: '我的信息',
      key: 'SelfInfo'
    },
  ]
  const activeName = ref('ProjectDonation')
  function isMobile() {
    return navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
  }
  console.log(isMobile())
</script>
<script lang="ts">
  import ProjectDonation from './ProjectDonation.vue'
  import PublicInfo from './PublicInfo.vue'
  import SelfInfo from './SelfInfo.vue'

  export default {
    components: {
      ProjectDonation,
      PublicInfo,
      SelfInfo
    }
  }
</script>
<style lang="less" scoped>
.mobile-radio{
  width: 100%;
  .el-radio-button{
    flex: 1;
    ::v-deep(.el-radio-button__inner){
      width: 100%
    }
  }
}
</style>
