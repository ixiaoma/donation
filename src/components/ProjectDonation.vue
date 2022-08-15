<template>
  <el-row :gutter="30">
    <el-col :span="8" v-for="(item, index) in 20" :key="index">
      <el-card :body-style="{ padding: '0px' }">
        <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image"/>
        <div style="padding: 14px">
          <div>
            <span class="title">{{item.title}}</span>
            <span class="title">{{item.donationNum}}人已捐</span>
          </div>
          <div>{{item.description}}</div>
          <div>
            <el-icon><Apple /></el-icon>
            <span>累计筹款</span>
            <span>¥{{item.donationMoney}}</span>
          </div>
          <div>
            <el-icon><Apple /></el-icon>
            <span>募捐机构</span>
            <span>¥{{item.donationOrg}}</span>
          </div>
        </div>
      </el-card>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup name="ProjectDonation">
import { ref } from 'vue'

const currentDate = ref(new Date())
</script>

<style>
.time {
  font-size: 12px;
  color: #999;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.button {
  padding: 0;
  min-height: auto;
}

.image {
  width: 100%;
  max-height: 100px;
  display: block;
}
</style>
