<template>
  <el-tabs v-model="activeName" :stretch="isMobile()" class="donation-tabs">
    <el-tab-pane v-for="item in tabList" :label="item.label" :name="item.key" >
      <component :is="item.key"></component>
    </el-tab-pane>
  </el-tabs>
</template>
<script lang="ts" setup>
  import { ref } from 'vue';

  import { isMobile } from '../libs/utils'

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
  ::v-deep(.el-tabs__header){
    margin: 0
  }
  ::v-deep(.el-tabs__nav-scroll){
      padding: 0 30px;
  }
  ::v-deep(.el-tabs__nav-wrap::after){
    display: none;
  }
</style>
