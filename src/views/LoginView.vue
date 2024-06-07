<script setup lang="ts">
import { reactive } from 'vue'

type IForm = {
  username: string
  password: string
}


  const form = reactive<IForm>({
    username: '',
    password: ''
    })

  const onSubmit = () => {
  }
</script>

<template>
  <main>
    <h1>Sign in</h1>
		<el-form :model="form" label-width="auto" style="max-width: 300px; margin-top: 20vh">
    <el-form-item label="Login" required >
      <el-input v-model="form.username" placeholder="Login" clearable />
    </el-form-item>
    <el-form-item label="Password" required >
      <el-input type='password' v-model="form.password" placeholder="Password" show-password clearable />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="onSubmit">Sign In</el-button>
    </el-form-item>
    </el-form>
  </main>
</template>
