<template>
  <el-radio-group v-model="selectRadio" :class="isMobile() ? 'mobile-radio' : ''">
    <el-radio-button label="项目捐赠" />
    <el-radio-button label="公开信息" />
    <el-radio-button label="我的信息" />
  </el-radio-group>
  <ProjectDonation v-show="selectRadio === '项目捐赠'"/>
  <PublicInfo v-show="selectRadio === '公开信息'"/>
  <SelfInfo v-show="selectRadio === '我的信息'"/>
</template>
<script lang="ts" setup>
  import { ref } from 'vue';
  import ProjectDonation from './ProjectDonation.vue'
  import PublicInfo from './PublicInfo.vue'
  import SelfInfo from './SelfInfo.vue'

  const selectRadio = ref('项目捐赠')
  function isMobile() {
    return navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
  }
  console.log(isMobile())
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
