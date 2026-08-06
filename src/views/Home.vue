<script setup lang="ts">
import Product from "./Product.vue";
import ProductCart from "@/components/ProductCart.vue";
</script>

<template>
  <img src="/aifosblack.jpg" alt="Home Image" class="w-full h-auto" />
  <ProductCart
    variant="home"
    title="AIFOS 極輕擴充收納組 (彩色組) (未上巿. 勿下單)"
    image="/aifosblack.jpg"
    :originalPrice="99.99"
    :discountPrice="79.99"
    :discountPercentage="20"
    :rating="4.5"
  />
</template>
