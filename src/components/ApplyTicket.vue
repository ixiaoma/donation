<template>
  <el-form
    ref="ruleFormRef"
    :model="ruleForm"
    label-position="top"
    :rules="rules"
    label-width="120px"
    class="invoice-form"
    :size="formSize"
    status-icon
  >
    <el-form-item label="手机号" prop="name">
      <el-input v-model="ruleForm.name" />
    </el-form-item>
    <el-form-item label="总金额" prop="name">
      <span class="red-text">1000元</span>
      <!-- <el-input v-model="ruleForm.name" /> -->
    </el-form-item>
    <el-form-item label="Resources" prop="resource">
      <el-radio-group v-model="ruleForm.resource">
        <el-radio label="Sponsorship" />
        <el-radio label="Venue" />
      </el-radio-group>
    </el-form-item>
    <el-form-item label="企业名称" prop="name">
      <el-input v-model="ruleForm.name" placeholder="请输入企业名称"/>
    </el-form-item>
    <el-form-item label="社会信用代码" prop="name">
      <el-input v-model="ruleForm.name" placeholder="请输入社会信用代码"/>
    </el-form-item>
    <el-form-item label="电子邮箱" prop="name">
      <el-input v-model="ruleForm.name" placeholder="请输入电子邮箱"/>
    </el-form-item>
    <el-form-item label="备注" prop="desc">
      <el-input v-model="ruleForm.desc" type="textarea" placeholder="请输入备注"/>
    </el-form-item>
    <el-button class="comfirm-btn" type="primary" @click="submitForm(ruleFormRef)">确定</el-button>
  </el-form>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

const formSize = ref('default')
const ruleFormRef = ref<FormInstance>()
const ruleForm = reactive({
  name: 'Hello',
  region: '',
  count: '',
  date1: '',
  date2: '',
  delivery: false,
  type: [],
  resource: '',
  desc: '',
})

const rules = reactive<FormRules>({
  name: [
    { required: true, message: 'Please input Activity name', trigger: 'blur' },
    { min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' },
  ],
  region: [
    {
      required: true,
      message: 'Please select Activity zone',
      trigger: 'change',
    },
  ],
  count: [
    {
      required: true,
      message: 'Please select Activity count',
      trigger: 'change',
    },
  ],
  date1: [
    {
      type: 'date',
      required: true,
      message: 'Please pick a date',
      trigger: 'change',
    },
  ],
  date2: [
    {
      type: 'date',
      required: true,
      message: 'Please pick a time',
      trigger: 'change',
    },
  ],
  type: [
    {
      type: 'array',
      required: true,
      message: 'Please select at least one activity type',
      trigger: 'change',
    },
  ],
  resource: [
    {
      required: true,
      message: 'Please select activity resource',
      trigger: 'change',
    },
  ],
  desc: [
    { required: true, message: 'Please input activity form', trigger: 'blur' },
  ],
})

const submitForm = async (formEl: FormInstance | undefined) => {
  if (!formEl) return
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!', fields)
    }
  })
}

const resetForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.resetFields()
}

const options = Array.from({ length: 10000 }).map((_, idx) => ({
  value: `${idx + 1}`,
  label: `${idx + 1}`,
}))
</script>
<style lang="less" scoped>
.invoice-form{
  padding: 0.2rem;
  ::v-deep(.el-input__wrapper),::v-deep(.el-textarea__inner){
    background-color: inherit;
    box-shadow: none;
    &:hover{
      box-shadow: none;
    }
  }
  .el-form-item{
    border-bottom: 1px solid #D6DCE5;
    ::v-deep(.el-form-item__label){
      color: #A7B1BC;
    }
  }
  .comfirm-btn{
    width: 100%;
  }
}
</style>