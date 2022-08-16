<script setup lang="ts">
import zhCn from 'element-plus/lib/locale/lang/zh-cn'

import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <el-config-provider :locale="zhCn">
    <HelloWorld />
  </el-config-provider>
</template>

<style lang="less">
  @import url('./styles/common.less');
</style>
