<script setup lang="ts">
import { ref, computed } from 'vue'
const minPrice = ref(0)
const maxPrice = ref(50000)

const currentMin = ref(0)
const currentMax = ref(50000)

const minProgress = computed(() => {
  return (Math.min(currentMin.value, currentMax.value) / maxPrice.value) * 100
})
const maxProgress = computed(() => {
  return (Math.max(currentMin.value, currentMax.value) / maxPrice.value) * 100
})
</script>
<template>
  <div class="mb-10">
    <h3
      class="text-[11px] text-gray-400 font-bold uppercase tracking-widest mb-6"
    >
      Filter By Price
    </h3>

    <div class="flex justify-between items-center mb-6">
      <div
        class="bg-gray-100 rounded-full px-4 py-1 text-xs font-bold text-gray-800"
      >
        ${{
          Math.min(currentMin, currentMax).toLocaleString(undefined, {
            minimumFractionDigits: 0,
            maximumFractionDigits: 2,
          })
        }}
      </div>
      <div
        class="bg-gray-100 rounded-full px-4 py-1 text-xs font-bold text-gray-800"
      >
        ${{
          Math.max(currentMin, currentMax).toLocaleString(undefined, {
            minimumFractionDigits: 2,
            maximumFractionDigits: 2,
          })
        }}
      </div>
    </div>

    <!-- Dual Range Slider -->
    <div class="relative h-6 flex items-center mb-8">
      <div class="absolute w-full h-[2px] bg-gray-200"></div>
      <div
        class="absolute h-[2px] bg-black"
        :style="{ left: `${minProgress}%`, right: `${100 - maxProgress}%` }"
      ></div>

      <div
        class="absolute w-3.5 h-3.5 bg-white border-[2px] border-black rounded-full -translate-x-1/2 pointer-events-none z-30"
        :style="{ left: `${minProgress}%` }"
      ></div>
      <div
        class="absolute w-3.5 h-3.5 bg-white border-[2px] border-black rounded-full -translate-x-1/2 pointer-events-none z-30"
        :style="{ left: `${maxProgress}%` }"
      ></div>

      <input
        type="range"
        :min="minPrice"
        :max="maxPrice"
        v-model="currentMin"
        class="absolute inset-0 w-full h-full opacity-0 cursor-pointer pointer-events-none z-40 m-0 [&::-webkit-slider-thumb]:pointer-events-auto [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-[14px] [&::-webkit-slider-thumb]:h-[14px] [&::-webkit-slider-thumb]:rounded-full [&::-moz-range-thumb]:pointer-events-auto [&::-moz-range-thumb]:w-[14px] [&::-moz-range-thumb]:h-[14px] [&::-moz-range-thumb]:rounded-full [&::-moz-range-thumb]:border-none"
      />
      <input
        type="range"
        :min="minPrice"
        :max="maxPrice"
        v-model="currentMax"
        class="absolute inset-0 w-full h-full opacity-0 cursor-pointer pointer-events-none z-50 m-0 [&::-webkit-slider-thumb]:pointer-events-auto [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-[14px] [&::-webkit-slider-thumb]:h-[14px] [&::-webkit-slider-thumb]:rounded-full [&::-moz-range-thumb]:pointer-events-auto [&::-moz-range-thumb]:w-[14px] [&::-moz-range-thumb]:h-[14px] [&::-moz-range-thumb]:rounded-full [&::-moz-range-thumb]:border-none"
      />
    </div>
  </div>
</template>
