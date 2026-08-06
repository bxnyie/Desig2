<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  variant: {
    type: String,
    default: "home",
  },
  title: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
  originalPrice: {
    type: Number,
    required: true,
  },
  discountPrice: {
    type: Number,
    required: true,
  },
  discountPercentage: {
    type: Number,
    required: true,
  },
  rating: {
    type: Number,
    required: true,
  },
});

const isHome = computed(() => props.variant === "home");
</script>

<template>
  <div class="size-96 bg-zinc-200 rounded-md">
    <div class="w-11 h-6 bg-slate-50 rounded-md">
      <div
        v-if="isHome"
        class="text-red-500 text-sm font-medium font-['DM_Sans']"
      >
        SALE
      </div>
    </div>
    <div class="text-slate-900 text-2xl font-bold font-['DM_Sans'] mt-60">
      {{ props.title }}
    </div>
    <div class="flex flex-row items-center justify-center gap-[20px] mt-2">
      <div
        class="text-left text-red-500 text-base font-medium font-['DM_Sans']"
      >
        {{ "$" + props.discountPrice.toFixed(2) }}
      </div>
      <div
        class="text-right text-gray-400 text-base font-medium font-['DM_Sans']"
      >
        {{ "$" + props.originalPrice.toFixed(2) }}
      </div>
    </div>
  </div>
</template>
