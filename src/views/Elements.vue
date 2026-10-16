
<script setup lang="ts">
import { ref, computed } from 'vue'

const selectedColor = ref('Oatmeal')
const selectedSize = ref('M')
const quantity = ref(1)
const wishlist = ref(false)
const selectedFilter = ref('All Reviews')
const addedToBag = ref(false)

const colors = [
  { name: 'Oatmeal', hex: '#e5e0d4' },
  { name: 'White', hex: '#ffffff' },
  { name: 'Black', hex: '#303030' }
]

const reviews = [
  {
    name: 'Alex',
    date: 'Oct 5, 2026',
    rating: 5,
    title: 'An easy everyday favorite',
    comment: 'Soft and comfortable. The relaxed fit works well with jeans.'
  },
  {
    name: 'Jamie',
    date: 'Oct 3, 2026',
    rating: 5,
    title: 'Great fit',
    comment: 'The oatmeal color is easy to match, and the tee feels lightweight.'
  },
  {
    name: 'Taylor',
    date: 'Oct 1, 2026',
    rating: 4,
    title: 'Nice basic tee',
    comment: 'Comfortable for everyday wear. I would prefer a slightly shorter length.'
  }
]

const filteredReviews = computed(() => {
  if (selectedFilter.value === '5 Stars') {
    return reviews.filter(review => review.rating === 5)
  }

  if (selectedFilter.value === '4 Stars') {
    return reviews.filter(review => review.rating === 4)
  }

  return reviews
})

const emit = defineEmits(['navigate'])

function addToBag() {
  addedToBag.value = true
  // Connect 
}
</script>

<template>
  <div class="bg-white min-h-screen text-[#171717]">

    <div class="max-w-[1200px] mx-auto px-6 py-2">

      <!-- PRODUCT SECTION -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-[55px]">

        <!-- PRODUCT IMAGE -->
        <div class="bg-[#f5f5f5] w-full h-[550px] flex items-center justify-center">

          <svg
            viewBox="0 0 400 400"
            class="w-[85%] h-[85%]"
          >
            <path
              d="M100 70 L145 60 Q200 125 255 60 L300 70
                 L350 130 L310 170 L275 135
                 L275 330 L125 330 L125 135
                 L90 170 L50 130 Z"
              :fill="colors.find(c => c.name === selectedColor)?.hex"
              stroke="#66635d"
              stroke-width="2.5"
            />
            <path
              d="M145 60 Q200 145 255 60
                 Q200 110 145 60"
              fill="none"
              stroke="#77746d"
              stroke-width="3"
            />
          </svg>

        </div>

        <!-- PRODUCT INFORMATION -->
        <div>

          <p class="text-[11px] text-gray-500 uppercase mb-3">
            TOPS / COTTON ESSENTIALS
          </p>

          <h1 class="text-[32px] font-semibold mb-3">
            Cotton Oversized Tee
          </h1>

          <p class="text-[22px] mb-3">
            $40.00
          </p>

          <div class="flex items-center gap-2 text-[13px] mb-4">
            <span class="text-[17px]">★★★★★</span>
            <span>4.7 · 3 sample reviews</span>
          </div>

          <p class="text-[14px] mb-5">
            A relaxed everyday tee with a soft cotton feel.
          </p>

          <!-- COLOR -->
          <p class="text-[14px] mb-3">
            Color: {{ selectedColor }}
          </p>

          <div class="flex gap-2 mb-5">
            <button
              v-for="color in colors"
              :key="color.name"
              @click="selectedColor = color.name"
              :style="{ backgroundColor: color.hex }"
              :class="selectedColor === color.name
                ? 'border-black'
                : 'border-gray-300'"
              class="w-6 h-6 rounded-full border-2"
            ></button>
          </div>

          <!-- SIZE -->
          <div class="mb-5">
            <p class="text-[14px] mb-2">
              Size: {{ selectedSize }} (preview)
            </p>

            <div class="flex gap-2">
              <button
                v-for="size in ['S', 'M', 'L', 'XL']"
                :key="size"
                @click="selectedSize = size"
                :class="selectedSize === size
                  ? 'border-black bg-black text-white'
                  : 'border-gray-300'"
                class="border px-4 py-1 text-[12px]"
              >
                {{ size }}
              </button>
            </div>
          </div>

          <!-- QUANTITY -->
          <div class="mb-5">
            <p class="text-[14px] mb-2">
              Quantity: {{ quantity }} (preview)
            </p>

            <div class="flex items-center gap-4">
              <button
                @click="quantity = Math.max(1, quantity - 1)"
                class="border px-3 py-1"
              >
                -
              </button>

              <span>{{ quantity }}</span>

              <button
                @click="quantity++"
                class="border px-3 py-1"
              >
                +
              </button>
            </div>
          </div>

          <!-- ADD TO BAG -->
          <button
            @click="addToBag"
            class="bg-black text-white w-full h-[43px] text-[13px] mb-4"
          >
            {{ addedToBag ? 'Added to Bag ✓' : 'Add to Bag' }}
          </button>

          <!-- WISHLIST -->
          <button
            @click="wishlist = !wishlist"
            class="text-[13px] mb-5"
          >
            {{ wishlist ? '♥ Added to Wishlist' : '♡ Add to Wishlist' }}
          </button>

          <!-- PRODUCT DETAILS -->
          <h3 class="font-semibold text-[17px] mb-3">
            Product Details
          </h3>

          <p class="text-[13px] mb-5">
            Relaxed fit · Crew neckline · Short sleeves
          </p>

          <!-- FABRIC -->
          <h3 class="font-semibold text-[17px] mb-3">
            Fabric & Care
          </h3>

          <p class="text-[13px] mb-5">
            Sample specification: 100% cotton. Machine wash cold.
          </p>

          <!-- SHIPPING -->
          <h3 class="font-semibold text-[17px] mb-3">
            Shipping & Returns
          </h3>

          <p class="text-[13px] mb-5">
            Delivery and return options are shown at checkout.
          </p>

          <!-- BACK -->
          <button
            @click="emit('navigate', 'products')"
            class="bg-black text-white px-10 py-3 text-[13px]"
          >
            Back to Products
          </button>

        </div>
      </div>

      <!-- CUSTOMER REVIEWS -->
      <div class="mt-[60px]">

        <h2 class="text-[25px] font-semibold mb-4">
          Customer Reviews
        </h2>

        <p class="text-[11px] text-gray-400 mb-4">
          Sample reviews for this prototype
        </p>

        <!-- RATING SUMMARY -->
        <div class="flex gap-[100px] mb-6">

          <div>
            <h2 class="text-[32px] font-semibold">
              4.7 / 5
            </h2>

            <p class="text-[23px] my-2">
              ★★★★★
            </p>

            <p class="text-[12px] text-gray-500">
              Based on 3 sample reviews
            </p>
          </div>

          <!-- RATING BARS -->
          <div class="w-[350px]">

            <div
              v-for="star in [5, 4, 3, 2, 1]"
              :key="star"
              class="flex items-center gap-3 mb-2 text-[12px]"
            >
              <span class="w-6">{{ star }} ★</span>

              <div class="bg-gray-200 h-[5px] flex-1 rounded-full">
                <div
                  class="bg-black h-full rounded-full"
                  :style="{
                    width: (reviews.filter(r => r.rating === star).length / 3 * 100) + '%'
                  }"
                ></div>
              </div>

              <span class="text-gray-500 w-3">
                {{ reviews.filter(r => r.rating === star).length }}
              </span>
            </div>

          </div>
        </div>

        <!-- FILTER BUTTONS -->
        <div class="flex gap-3 mb-5">

          <button
            v-for="filter in ['All Reviews', '5 Stars', '4 Stars']"
            :key="filter"
            @click="selectedFilter = filter"
            :class="selectedFilter === filter
              ? 'bg-black text-white'
              : 'bg-[#f5f5f5] text-black'"
            class="px-4 py-3 text-[12px] rounded"
          >
            {{ filter }}
            ({{
              filter === 'All Reviews'
                ? reviews.length
                : reviews.filter(r => r.rating === Number(filter[0])).length
            }})
          </button>

        </div>

        <!-- REVIEW CARDS -->
        <div
          v-for="review in filteredReviews"
          :key="review.name"
          class="border border-gray-200 p-5 mb-4"
        >

          <p class="text-[12px] mb-3">
            {{ review.name }} · {{ review.date }}
          </p>

          <p class="text-[18px] mb-3">
            {{ '★'.repeat(review.rating) }}{{ '☆'.repeat(5 - review.rating) }}
          </p>

          <h3 class="text-[15px] font-semibold mb-3">
            {{ review.title }}
          </h3>

          <p class="text-[13px] text-gray-500">
            {{ review.comment }}
          </p>

        </div>

      </div>

    </div>

  </div>
</template>
