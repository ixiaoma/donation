<template>
  <el-tabs v-model="activeName" :class="['donation-tabs', isMobile() ? 'mobile-tabs' : '']">
    <el-tab-pane v-for="item in tabList" :label="item.label" :name="item.key" >
      <component :is="item.key"></component>
    </el-tab-pane>
  </el-tabs>
</template>
<script lang="ts" setup>
  import { ref } from 'vue';

  import { isMobile } from '../utils/commonUtil'

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
.mobile-tabs{
  width: 100%;
  ::v-deep(.el-tabs__nav){
    width: 100%;
    display: flex;
    .el-tabs__item{
      flex: 1;
      text-align: center;
    }
  }
}
</style>
