<template>
  <div>
  <FormProvider :form="form">
    <SchemaField :schema="schema" />
    <Submit @submit="onSubmit">提交</Submit>
  </FormProvider>
  <button  @click="manualSubmit">手动触发</button>
</div>
</template>

<script setup lang="ts">
import { createForm } from '@formily/core'
import { createSchemaField, FormProvider } from '@formily/vue'
import { FormItem, Input, Submit, FormGrid } from '@formily/element-plus'

const schema = {
  type: 'object',
  properties: {
    grid: {
      type: 'void',
      'x-component': 'FormGrid',
      'x-component-props': {
      },
      properties: {
        usename: {
          type: 'string',
          title: '用户名（修改required错误信息）',
          'x-decorator': 'FormItem',
          'x-component': 'Input',
          'x-validator': {
            required: true,
            message: '请输入'
          },
        },
        password: {
          type: 'string',
          title: '密码（多条件判断）',
          'x-decorator': 'FormItem',
          'x-component': 'Input',
          'x-validator': [{
            required: true,
            message: '请输入'
          }, {
            maximum: 5,
            message: '最多5位数'
          }],
        }
      },
    },
  },
}

const form = createForm()
const { SchemaField } = createSchemaField({
  components: {
    FormItem,
    Input,
    FormGrid,
  },
})

const onSubmit = (value) => {
  console.log(value)
}
const manualSubmit = (value) => {
  console.log(form)
  form.submit().then(() => {
    alert(`提交值：${JSON.stringify(form.values)}`)
  }).catch(res => {
    console.log(res)
  })
}
</script>