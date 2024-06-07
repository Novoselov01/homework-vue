<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <el-menu
    ellipsis
    class="el-menu-popper-demo"
    mode="horizontal"
    :popper-offset="16"
  >
  <el-menu-item index="0"><router-link to='/'><img
        style="width: 100px"
        src="@/assets/img/Your-Logo-here.png"
        alt="logo"
      /></router-link></el-menu-item>
  <div class="flex-grow" />
  <el-menu-item index="1"><router-link to='/about'>About</router-link></el-menu-item>
  <el-menu-item index="2"><router-link to='/catalog'>Catalog</router-link></el-menu-item>
  <el-menu-item index="3"><router-link to='/login'>Sign in</router-link></el-menu-item>
</el-menu>
    </div>
  </header>

  <RouterView />
  <el-backtop :right="70" :bottom="70" />
</template>

<style scoped>
a {
  text-decoration: none
}
.flex-grow {
  flex-grow: 0.9;
}
</style>
