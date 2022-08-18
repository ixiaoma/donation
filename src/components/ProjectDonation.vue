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
                <span class="icon-text">
                  <img src="../assets/icon/money.png" />
                  累计筹款
                </span>
                <span>
                  <span class="red-text">{{item.money}}</span>元
                </span>
              </div>
              <div class="flex-between">
                <span class="icon-text">
                  <img src="../assets/icon/org.png" />
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
    <div v-else v-infinite-scroll="loadData" class="infinite-list mobile-style" style="overflow: auto">
      <div class="mobile-shadow"></div>
      <div class="infinite-list-item" v-for="(item, index) in donationList" :key="index">
          <div class="top-info flex-between">
            <div class="left-con">
              <div class="top-label mobile-top-label">{{item.people}}人已捐</div>
              <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image"/>
            </div>
            <div class="text-content">
              <div class="title ellipsis-text">{{item.title}}</div>
              <div class="desc">{{item.description}}</div>
            </div>
          </div>
          <div class="flex-between">
              <span>
                <img src="../assets/icon/money.png" />
                累计筹款
              </span>
              <span>
                <span class="red-text">{{item.money}}</span>元
              </span>
            </div>
            <div class="flex-between">
              <span>
                <img src="../assets/icon/org.png" />
                募捐机构
              </span>
              <span>
                <span>{{item.org}}</span>
              </span>
            </div>
        </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { isMobile } from '../libs/utils'

const isPc = !isMobile()

const currentPage = ref(1)
const pageSize = ref(12)
const total = ref(100)
const donationList = ref([
  {
    title: '大病家庭希望之光',
    description: '王宇龙，出生于2000年2月13日，内蒙古呼和浩特市新城区东影北街舍楼。',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },
  {
    title: '大病家庭希望之光',
    description: '王宇龙，出生于2000年2月13日，内蒙古呼和浩特市新城区东影北街舍楼。',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },{
    title: '大病家庭希望之光',
    description: '王宇龙，出生于2000年2月13日，内蒙古呼和浩特市新城区东影北街舍楼。',
    money: 20000,
    org: '北京红十字会',
    people: 566
  },{
    title: '大病家庭希望之光',
    description: '王宇龙，出生于2000年2月13日，内蒙古呼和浩特市新城区东影北街舍楼。',
    money: 20000,
    org: '北京红十字会',
    people: 566
  }
])

function handleCurrentChange(val){
  console.log(val)
}

function loadData(){

}
</script>

<style lang="less" scoped>
.donation-list{
  .top-label{
    position: absolute;
    right: 0;
    padding: 0.06rem 0.08rem;
    font-size: 12px;
    color: #fff;
    background: linear-gradient(168deg, #FF7373 0%, #F23061 100%);
    box-shadow: 8px 8px 15px 0px rgba(203,0,34,0.1200);
    border-radius: 0px 0px 0px 10px;
  }
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
    .text-content{
      padding: 20px;
      .title{
        font-weight: 500;
        font-size: 18px;
      }
      .desc{
        color: #AFAFAF;
        border-bottom: 1px dashed #D6DCE5;
      }
      .icon-text{
        display: flex;
        align-items: center;
        img{
          width: 18px;
          margin-right: 5px;
        }
      }
    }
  }
  .mobile-shadow{
    box-shadow: 0px 10px 26px 0px rgba(19,21,25,0.06);    
  }
  .mobile-style {
    .left-con{
      position: relative;
      width: 36%;
      .image{
        width: 100%;
      }
    }
    .top-info{
      align-items: flex-start;
      padding-bottom: 0.3rem;
      margin-bottom: 0.3rem;
      border-bottom: 1px dashed #D6DCE5;
    }
    .text-content{
      flex: 1;
      overflow: hidden;
      padding-left: 0.3rem;
      
      .title{
        font-size: 0.6rem;
        font-weight: 500;
        line-height: 1.5;
      }
      .desc{
        color: #AFAFAF;
      }
    }
    .flex-between{
      line-height: 2;
      span{
        font-size: 0.56rem;
        display: flex;
        align-items: center;
        img{
          display: block;
          width: 0.68rem;
          margin-right: 0.1rem;
        }
      }
    }
    & + .list-item {
      margin-top: 10px;
    }
  }
}

</style>
