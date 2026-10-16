
<script setup lang="ts">
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
  price: {
    type: Number,
    required: true,
  },
  rating: {
    type: Number,
    required: true,
  },
  reviews: {
    type: Number,
    required: true,
  },
  colors: {
    type: Array,
    default: () => [],
  },
});
</script>

<template>
  <div class="w-full">

    <!-- PRODUCT IMAGE -->
    <div class="w-full aspect-square bg-[#f6f6f6] overflow-hidden">
      <img
        :src="props.image"
        class="w-full h-full object-contain"
      />
    </div>

    <!-- PRODUCT TITLE -->
    <div class="text-[16px] font-medium mt-4">
      {{ props.title }}
    </div>

    <!-- PRICE -->
    <div class="text-[15px] mt-2">
      {{ "$" + props.price.toFixed(2) }}
    </div>

    <!-- RATING -->
    <div class="flex items-center gap-2 mt-2">
      <span class="text-[12px]">
        ★★★★★
      </span>

      <span class="text-[11px] text-gray-400">
        {{ props.rating }} ({{ props.reviews }} reviews)
      </span>
    </div>

    <!-- COLORS -->
    <div class="flex items-center gap-2 mt-3">
      <div
        v-for="color in props.colors"
        :key="color"
        class="w-[13px] h-[13px] rounded-full border border-gray-300"
        :style="{ backgroundColor: color }"
      ></div>
    </div>

    <!-- SAVE ITEM -->
    <button class="text-[12px] text-gray-400 mt-3 hover:text-black">
      ♡ Save item
    </button>

  </div>
</template>
