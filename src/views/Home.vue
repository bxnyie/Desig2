<script setup lang="ts">
import { ref, computed } from 'vue'
import Product from "./Product.vue";
import ProductCart from "@/components/ProductCart.vue";


const allProducts = Array.from({ length: 20 }, (_, i) => ({
  id: i,
  title: `Tracksuit Hyped ${i + 1}`,
  brand: 'Apple Cherry',
  price: 384,
  originalPrice: 454,
  isSale: true
}))

const itemsPerPage = 4
const currentPage = ref(0)
const totalPages = Math.ceil(allProducts.length / itemsPerPage)

const paginatedProducts = computed(() => {
  const start = currentPage.value * itemsPerPage
  return allProducts.slice(start, start + itemsPerPage)
})
</script>

<template>
  <img src="/aifosblack.jpg" alt="Home Image" class="w-full h-auto" />


  <div class="flex flex-row items-center justify-center gap-[50px] mt-[50px] ">
  
    <ProductCart
    v-for="product in paginatedProducts"
      variant="home"
      :title="product.title"
      :image="product.image"
      :originalPrice="product.originalPrice"
      :discountPrice="product.discountPrice"
      :discountPercentage="product.discountPercentage"
      :rating="product.rating"
    />
  </div>

  <!-- 小點點 -->
  <div class="flex justify-center gap-2 mt-4 mb-[50px]">
    <button
      v-for="i in totalPages"
      :key="i"
      @click="currentPage = i - 1"
      :class="[
        'w-8 h-8 rounded-full',
        currentPage === i - 1 ? 'bg-blue-500 text-white' : 'bg-gray-200 text-gray-700'
      ]"
    >
      {{ i }}
    </button>
  </div>


</template>
