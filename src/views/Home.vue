
<script setup lang="ts">
import { ref, computed } from 'vue'

const collections = [
  {
    name: 'Neutral Edit',
    image: '/neutral.jpg',
  },
  {
    name: 'Monochrome Edit',
    image: '/monochrome.jpg',
  },
  {
    name: 'Colorful Edit',
    image: '/colorful.jpg',
  },
]

const products = [
  {
    id: 1,
    name: 'Cotton Oversized Tee',
    price: 40,
    rating: 4.7,
    reviews: 17,
    image: '/product1.jpg',
    colors: ['#e5e0d4', '#a29a89', '#303638'],
  },
  {
    id: 2,
    name: 'Everyday Knit Sweater',
    price: 68,
    rating: 4.8,
    reviews: 32,
    image: '/product2.jpg',
    colors: ['#c4b8a8', '#8c7a68', '#dedbd3'],
  },
  {
    id: 3,
    name: 'Pleated Midi Skirt',
    price: 56,
    rating: 4.5,
    reviews: 45,
    image: '/product3.jpg',
    colors: ['#303638', '#aaa091'],
  },
  {
    id: 4,
    name: 'Relaxed Cotton Shirt',
    price: 62,
    rating: 4.8,
    reviews: 18,
    image: '/product4.jpg',
    colors: ['#d7e1e3', '#a4a9a8', '#f0eeea'],
  },
  {
    id: 5,
    name: 'Everyday Basic Tee',
    price: 38,
    rating: 4.6,
    reviews: 24,
    image: '/product5.jpg',
    colors: ['#eae4dd', '#333333'],
  },
]

const currentPage = ref(0)
const itemsPerPage = 4

const visibleProducts = computed(() => {
  const start = currentPage.value * itemsPerPage
  return products.slice(start, start + itemsPerPage)
})

const email = ref('')
const subscribed = ref(false)
const savedItems = ref<number[]>([])

function toggleSave(id: number) {
  if (savedItems.value.includes(id)) {
    savedItems.value = savedItems.value.filter(item => item !== id)
  } else {
    savedItems.value.push(id)
  }
}

function subscribe() {
  if (!email.value.trim()) return
  subscribed.value = true
}
</script>

<template>
  <main class="w-full bg-white text-[#242424]">

    <!-- menu SECTION -->
    <section class="w-full ">
      <div class="relative w-full overflow-hidden">
        <img
          src="/homepage.jpg"
          alt="Aifos Collection"
          class="h-[560px] w-full object-cover"
        />

        <div class="absolute inset-0 bg-black/25"></div>

        <div
          class="absolute left-[5%] top-1/2 max-w-[90%] -translate-y-1/2 text-white"
        >
          <p class="mb-4 text-[11px] uppercase tracking-[1px]">
            AIFOS | THE COLLECTION
          </p>

          <h1 class="mb-4 text-[36px] font-semibold leading-tight md:text-[44px]">
            Carry your own style.
          </h1>

          <p class="mb-5 text-[14px]">
            Discover prints and pieces for everyday living.
          </p>

          <button
            type="button"
            class="bg-white px-7 py-3 text-[13px] text-black transition hover:bg-gray-200"
          >
            Explore the Collection →
          </button>
        </div>
      </div>
    </section>

      

    <!-- EXPLORE COLLECTIONS -->
    <section class="mx-auto max-w-[1440px] px-[5%] mt-[65px]">

      <h2 class="text-[24px] font-semibold mb-5">
        Explore the Collections
      </h2>

      <div class="grid grid-cols-3 gap-6">

        <div
          v-for="collection in collections"
          :key="collection.name"
          class="cursor-pointer group"
        >

          <div class="overflow-hidden bg-[#f4f4f4]">
            <img
              :src="collection.image"
              :alt="collection.name"
              class="w-full aspect-[1.32] object-cover group-hover:scale-105 transition duration-300"
            />
          </div>

          <h3 class="text-[16px] font-medium mt-4">
            {{ collection.name }}
          </h3>

          <p class="text-[13px] mt-3 group-hover:underline">
            Discover →
          </p>

        </div>

      </div>

    </section>


    <!-- TOP ITEMS -->
    <section class="mx-auto max-w-[1440px] px-[5%] mt-[65px]">

      <div class="flex justify-between items-center mb-5">

        <h2 class="text-[24px] font-semibold">
          Top Items
        </h2>

        <a href="/products" class="text-[13px] hover:underline">
          View all →
        </a>

      </div>


      <div class="grid grid-cols-4 gap-7">

        <div
          v-for="product in visibleProducts"
          :key="product.id"
          class="group"
        >

          <!-- PRODUCT IMAGE -->
          <div class="w-full aspect-[0.93] bg-[#f6f6f6] overflow-hidden">

            <img
              :src="product.image"
              :alt="product.name"
              class="w-full h-full object-contain group-hover:scale-105 transition duration-300"
            />

          </div>

          <!-- PRODUCT INFO -->
          <div class="mt-4">

            <h3 class="text-[15px] font-medium">
              {{ product.name }}
            </h3>

            <p class="text-[15px] mt-2">
              ${{ product.price.toFixed(2) }}
            </p>

            <div class="flex items-center gap-2 mt-2">

              <span class="text-[13px]">
                ★★★★★
              </span>

              <span class="text-[12px] text-gray-400">
                {{ product.rating }}
                ({{ product.reviews }} reviews)
              </span>

            </div>

            <!-- COLORS -->
            <div class="flex gap-2 mt-3">

              <div
                v-for="color in product.colors"
                :key="color"
                :style="{ backgroundColor: color }"
                class="w-[13px] h-[13px] rounded-full border border-gray-300 cursor-pointer"
              ></div>

            </div>

            <!-- SAVE -->
            <button
              type="button"
              @click="toggleSave(product.id)"
              class="flex items-center gap-1 text-[12px] text-gray-400 mt-3 hover:text-black"
            >
              {{ savedItems.includes(product.id) ? '♥ Saved' : '♡ Save item' }}
            </button>

          </div>

        </div>

      </div>


      <!-- SHOP LINK -->
      <div class="mt-[50px]">
        <a href="/products" class="text-[13px] text-gray-500 hover:text-black">
          Shop all or get to explore more →
        </a>
      </div>

    </section>


    <!-- PROMOTIONAL BANNER -->
    <section class="mx-auto max-w-[1440px] px-[5%] mt-[65px]">

      <div class="bg-[#f7f7f7] px-9 py-9">

        <h2 class="text-[24px] font-semibold">
          Made to go with you.
        </h2>

        <p class="text-[14px] text-gray-500 mt-3">
          From everyday essentials to expressive prints,
          find your Aifos favorites.
        </p>

      </div>

    </section>


    <!-- NEWSLETTER -->
    <section
      class="mx-auto max-w-[1440px] px-[5%] mt-[80px] mb-[30px]"
    >

      <div class="flex justify-between items-center gap-8">

        <div>

          <h2 class="text-[24px] font-semibold">
            Stay in the loop.
          </h2>

          <p class="text-[14px] text-gray-500 mt-3">
            New collections and Aifos updates, straight to your inbox.
          </p>

        </div>

        <form
          @submit.prevent="subscribe"
          class="flex items-center border border-gray-300 w-[460px] h-[48px]"
        >

          <input
            v-model="email"
            type="email"
            placeholder="Your email address"
            required
            class="flex-1 min-w-0 px-4 outline-none text-[13px]"
          />

          <button
            type="submit"
            class="px-6 text-[13px] whitespace-nowrap"
          >
            Sign up →
          </button>

        </form>

      </div>

      <p
        v-if="subscribed"
        class="text-[13px] text-green-700 mt-3 text-right"
      >
        Thank you for signing up!
      </p>

    </section>

  </main>
</template>
