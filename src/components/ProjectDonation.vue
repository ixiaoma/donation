<template>
  <div class="donation-list">
    <div v-if="isPc">
      <el-row :gutter="30">
        <el-col :span="6" v-for="(item, index) in donationList" :key="index">
          <el-card :body-style="{ padding: '0px' }" class="list-item">
            <div class="top-label">{{item.people}}人已捐</div>
            <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image"/>
            <div class="text-content">
              <div class="title">{{item.title}}</div>
              <div class="desc pd-y-16">{{item.description}}</div>
              <div class="flex-between pd-y-16">
                <span>
                  <el-icon><Apple /></el-icon>
                  累计筹款
                </span>
                <span>
                  <span class="red-text">{{item.money}}</span>元
                </span>
              </div>
              <div class="flex-between">
                <span>
                  <el-icon><Apple /></el-icon>
                  募捐机构
                </span>
                <span>
                  <span>{{item.org}}</span>
                </span>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
      <div class="pagination-block">
        <el-pagination
          v-model:currentPage="currentPage"
          v-model:page-size="pageSize"
          layout="total, prev, pager, next, jumper"
          :total="total"
          @current-change="handleCurrentChange"
        />
      </div>
    </div>
    <div v-else>

    </div>
  </div>
</template>

<script lang="ts" setup name="ProjectDonation">
import { ref } from 'vue'
import { isMobile } from '../libs/utils'

const isPc = !isMobile()

const currentPage = ref(1)
const pageSize = ref(12)
const total = ref(100)
const donationList = ref([
  {
    title: '大病家庭希望之光',
    description: '11岁南通突患血癌，6年三好学生，盼望各',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },
  {
    title: '大病家庭希望之光',
    description: '11岁南通突患血癌，6年三好学生，盼望各',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },{
    title: '大病家庭希望之光',
    description: '11岁南通突患血癌，6年三好学生，盼望各',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },{
    title: '大病家庭希望之光',
    description: '11岁南通突患血癌，6年三好学生，盼望各',
    money: 20000,
    org: '北京红十字会',
    people: 566
  }
])

function handleCurrentChange(val){
  console.log(val)
}
</script>

<style lang="less" scoped>
.donation-list{
  .list-item{
    position: relative;
    color: #000000;
    border: none;
    border-radius: 0;
    box-shadow: 0px 2px 15px 0px rgba(160,165,180,0.1400);
    margin-bottom: 20px;
    .image {
      width: 100%;
      max-height: 220px;
      display: block;
    }
    .top-label{
      position: absolute;
      right: 0;
      padding: 6px 8px;
      font-size: 12px;
      color: #fff;
      background: linear-gradient(168deg, #FF7373 0%, #F23061 100%);
      box-shadow: 8px 8px 15px 0px rgba(203,0,34,0.1200);
      border-radius: 0px 0px 0px 10px;
    }
    .text-content{
      padding: 20px;
      .title{
        font-weight: 500;
        font-size: 18px;
      }
      .desc{
        font-size: 13px;
        color: #AFAFAF;
        border-bottom: 1px dashed #D6DCE5;
      }
    }
  }
}

</style>
