<!--  -->
<template>
  <div>
    <KForm
      :model="model"
      :rules="rules"
      ref="loginForm"
    >
      <KFormItem
        label="同户名"
        prop="username"
      >
        <KInput v-model="model.username"></KInput>
      </KFormItem>
      <KFormItem
        label="密码"
        prop="password"
      >
        <KInput
          v-model="model.password"
          type="password"
        ></KInput>
      </KFormItem>
      <KFormItem><button @click="onLogin">登录</button></KFormItem>

    </KForm>

    {{model}}
  </div>
</template>

<script>
import KInput from '@/components/form/KInput'
import KFormItem from '@/components/form/KFormItem'
import KForm from '@/components/form/KForm'
export default {
  data() {
    return {
      model: {
        username: 'tom',
        password: ''
      },
      rules: {
        username: [{ required: true, message: '用户名必填' }],
        password: [{ required: true, message: '密码必填' }]
      }
    }
  },
  components: {
    KInput,
    KFormItem,
    KForm
  },
  methods: {
    onLogin() {
      this.$refs.loginForm.validate((isValid) => {
        if (isValid) {
          alert("登录");
        }
        else {
          alert("有错");
        }
      })
    }
  },
}

</script>



<style  scoped></style>
