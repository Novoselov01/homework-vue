<script setup lang="ts">
import type { IProduct } from '@/interface/productInterface'
import { round } from '@/utils/round'
import axios from 'axios'
import { ElMessage } from 'element-plus'
import { reactive, ref } from 'vue'

const loading = ref<boolean>(true)
const products = reactive<IProduct[]>([])

axios.get('https://dummyjson.com/products')
.then(res => products.push(...res.data.products))
.catch(() => ElMessage.error('Oops, something wrong.'))
.finally(() => loading.value = false);

const getOldPrice = (price: number, discount: number) => round(price + price/100*discount)

</script>

<template>
  <main>
    <h1>Catalog</h1>
    <div v-if = 'products.length === 0 && !loading'>Catalog is empty</div>

    <div class='catalog' v-loading="loading">
    <el-card style="width: 400px; margin: 1rem" v-for='product in products' :key='product.id' >
    <img class='product-image' :src='product.images[0]' :alt="product.title"/>
    <div class='product-price'>
      <span class='price new' style='color: red; font-family: fantasy;'>{{ product.price }}$</span>
      <span class='price old' style='color: grey; text-decoration: line-through'>{{ getOldPrice(product.price, product.discountPercentage)}}$</span>
      <span class='price discount' style='color: red'>{{ product.discountPercentage}}%</span>
    </div>
    <div class='product-title'>{{ product.title }}</div>
   

    <template #footer>
      <el-button>Open</el-button>
      <el-button><el-icon><ShoppingCart /></el-icon><span>Add to cart</span> </el-button>
    </template>
  </el-card>
</div>
  </main>
</template>

<style scoped>
.catalog {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
.product-image{
  height: 200px;
  width: 200px;
}
.product-price{
  font-size: 24px
}
.price.old, .price.discount {
  font-size: 18px
  }
span.price{
  padding: 0.2rem
}
</style>
