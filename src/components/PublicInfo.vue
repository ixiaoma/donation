<template>
    <div class="public-info">
        <div class="top-search" v-if="!isPc">
            <el-input :prefix-icon="Search" placeholder="请输入募捐机构/捐赠人/捐赠金额"/>
        </div>
        <div v-if="isPc">
            <el-descriptions v-for="(item, index) in descList" :key="index" :title="item.title" class="desc-item">
                <el-descriptions-item label="捐赠单号:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="项目编号:">{{ item.no }}</el-descriptions-item>
                <el-descriptions-item label="货币:">
                    <span class="red-text">{{ item.huobi }}</span>
                </el-descriptions-item>
                <el-descriptions-item label="募捐机构:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="项目名称:">{{ item.no }}</el-descriptions-item>
                <el-descriptions-item label="金额:">
                    <span class="red-text">{{ item.huobi }}</span>
                </el-descriptions-item>
                <el-descriptions-item label="捐赠人:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="捐赠时间:">{{ item.no }}</el-descriptions-item>
                <el-descriptions-item label="单位:">
                    <span class="red-text">{{ item.huobi }}</span>
                </el-descriptions-item>
            </el-descriptions>
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
            <el-descriptions v-for="(item, index) in descList" :key="index" :title="`捐赠时间：${item.time}`" class="infinite-list-item" :column="1">
                <el-descriptions-item label="捐赠单号:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="募捐机构:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="捐赠人:">{{ item.danhao }}</el-descriptions-item>
                <el-descriptions-item label="项目名称:">{{ item.no }}</el-descriptions-item>
                <el-descriptions-item label="捐赠金额:">
                    <span class="red-text">{{ item.huobi }}</span>
                </el-descriptions-item>
            </el-descriptions>
        </div>
    </div>
</template>
<script lang="ts" setup>
    import { ref } from 'vue';
    import { isMobile } from '../libs/utils'
    import { Search } from '@element-plus/icons-vue'

    const isPc = !isMobile()

    const currentPage = ref(1)
    const pageSize = ref(12)
    const total = ref(100)

    const descList = ref([
        {
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY',
            time: new Date().toLocaleString()
        },{
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY',
            time: new Date().toLocaleString()
        },{
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY',
            time: new Date().toLocaleString()
        }
    ])

    function handleCurrentChange(val){
        console.log(val)
    }
</script>
<style lang="less">
.public-info{
    .el-descriptions__label, .el-descriptions__content{
        color: #8D8F94;
    }
    .desc-item{
        box-shadow: 0px 0.02px 0.15px 0px rgba(160,165,180,0.1400);
        margin-bottom: 0.2px;
        // padding: 30px 30px 18px;
        padding: 0.5rem;
        &::before{
            content: '';
            position: absolute;
            left: 0;
            margin-top: 5px;
            width: 5px;
            height: 18px;
            background: #E50717;
            border-radius: 0px 2px 2px 0px
        }
        .el-descriptions__title{
            font-size: 20px;
            font-weight: 600;
        }
    }
    .top-search{
        width: 100%;
        background-color: #fff;
        border-top: 1px solid #D6DCE5;
        box-shadow: 0px 12px 26px 0px rgba(19,21,25,0.06);
        padding: 0.3rem 0;
        margin-bottom: 15px;
        .el-input__wrapper{
            margin: 0 0.3rem;
            background: #F7F8FA;
            box-shadow: 0px 12px 26px 0px rgba(19,21,25,0.06);
            border-radius: 38px;
        }
    }
    .mobile-style{
        position: relative;
        .el-descriptions__header{
            margin-left: -0.3rem;
            margin-right: -0.3rem;
            padding: 0.3rem;
            border-bottom: 1px solid #D6DCE5;
        }
        .el-descriptions__title{
            padding-bottom: 0.2rem;
            &::before{
                content: '';
                position: absolute;
                left: 0.3rem;
                margin-top: 3px;
                width: 5px;
                height: 18px;
                background: #E50717;
                border-radius: 0px 2px 2px 0px
            }
        }
    }
}
</style>