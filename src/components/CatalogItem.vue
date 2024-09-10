<script setup lang="ts">
import { round } from '@/utils/round'


const props = defineProps(['products'])
const getOldPrice = (price: number, discount: number) => round(price + price/100*discount)
</script>

<template>
	    <el-card style="width: 400px; margin: 1rem" v-for='product in props.products' :key='product.id' >
    <img class='product-image' :src='product.images[0]' :alt="product.title"/>
    <div class='product-price'>
      <span class='price new' style='color: red; font-family: fantasy;'>{{ product.price }}$</span>
      <span class='price old' style='color: grey; text-decoration: line-through'>{{ getOldPrice(product.price, product.discountPercentage)}}$</span>
      <span class='price discount' style='color: red'>-{{ product.discountPercentage}}%</span>
    </div>
    <div class='product-title'>{{ product.title }}</div>
   

    <template #footer>
      <el-button>Open</el-button>
      <el-button><el-icon><ShoppingCart /></el-icon><span>Add to cart</span> </el-button>
    </template>
  </el-card>
</template>

<style>
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
}</style>