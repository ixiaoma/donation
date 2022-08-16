<template>
    <div class="public-info">
        <el-descriptions v-for="(item, index) in descList" :key="index" :title="item.title" class="desc-item" :column="isMobile() ? 1 : 3">
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
</template>
<script lang="ts" setup>
    import { ref } from 'vue';
    import { isMobile } from '../libs/utils'

    const currentPage = ref(1)
    const pageSize = ref(12)
    const total = ref(100)

    const descList = ref([
        {
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY'
        },{
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY'
        },{
            title: '摔伤昏迷诺宝快醒来',
            danhao: '531100005960786022001',
            no: '18100000000',
            huobi: 'CNY'
        }
    ])

    function handleCurrentChange(val){
        console.log(val)
    }
</script>
<style lang="less">
.desc-item{
    box-shadow: 0px 2px 15px 0px rgba(160,165,180,0.1400);
    margin-bottom: 20px;
    padding: 0.3rem;
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
    .el-descriptions__label, .el-descriptions__content{
        font-size: 13px;
        color: #8D8F94;
    }
}
</style>