
<script setup lang="ts">
import { ref, computed } from 'vue'

type CartItem = {
  id: number
  name: string
  price: number
  color: string
  size: string
  image: string
  quantity: number
}

const emit = defineEmits<{
  (e: 'navigate', page: string): void
}>()

const products = ref<CartItem[]>([
  {
    id: 1,
    name: 'Cotton Oversized Tee',
    price: 40,
    color: 'Oatmeal',
    size: 'M',
    image: '/product1.jpg',
    quantity: 1,
  },
  {
    id: 2,
    name: 'Everyday Knit Sweater',
    price: 68,
    color: 'Sand',
    size: 'M',
    image: '/product2.jpg',
    quantity: 1,
  },
  {
    id: 3,
    name: 'Pleated Midi Skirt',
    price: 56,
    color: 'Charcoal',
    size: 'M',
    image: '/product3.jpg',
    quantity: 1,
  },
])

const wishlist = ref<CartItem[]>([])
const promoCode = ref('')
const promoMessage = ref('')
const discountRate = ref(0)

const itemCount = computed(() =>
  products.value.reduce((total, item) => total + item.quantity, 0)
)

const subtotal = computed(() =>
  products.value.reduce(
    (total, item) => total + item.price * item.quantity,
    0
  )
)

const shipping = computed(() =>
  products.value.length > 0 ? 8 : 0
)

const discount = computed(() =>
  subtotal.value * discountRate.value
)

const total = computed(() =>
  subtotal.value + shipping.value - discount.value
)

function increaseQuantity(item: CartItem) {
  item.quantity++
}

function decreaseQuantity(item: CartItem) {
  if (item.quantity > 1) {
    item.quantity--
  }
}

function removeItem(id: number) {
  products.value = products.value.filter(item => item.id !== id)
}

function moveToWishlist(item: CartItem) {
  wishlist.value.push({ ...item })
  removeItem(item.id)
}

function applyPromoCode() {
  promoMessage.value = 'Promo code validation is not available yet.'
  discountRate.value = 0
}

function formatPrice(price: number) {
  return '$' + price.toFixed(2)
}

function proceedToCheckout() {
  if (products.value.length === 0) return
  emit('navigate', 'checkout')
}

function continueShopping() {
  emit('navigate', 'products')
}
</script>

<template>
  <div class="min-h-screen bg-white text-[#171717]">
    <div class="mx-auto max-w-[1240px] px-[30px] pt-[85px] pb-[80px]">

      <!-- Progress -->
      <div class="mb-[20px] flex flex-wrap items-center gap-[25px] text-[13px]">
        <span class="font-semibold text-black">
          01&nbsp; Shopping Cart
        </span>

        <span class="text-gray-400">—</span>

        <span class="text-gray-400">
          02&nbsp; Checkout
        </span>

        <span class="text-gray-400">—</span>

        <span class="text-gray-400">
          03&nbsp; Confirmation
        </span>
      </div>

      <!-- Title -->
      <h1 class="text-[32px] font-semibold tracking-[-0.5px]">
        Your Shopping Cart
      </h1>

      <p class="mt-[14px] text-[13px] text-[#888]">
        {{ itemCount }} items · Sample order
      </p>

      <!-- Main layout -->
      <div
        class="mt-[20px] grid grid-cols-1 items-start gap-[40px] lg:grid-cols-[minmax(0,704px)_minmax(0,358px)]"
      >

        <!-- LEFT: Products -->
        <div>

          <!-- Empty cart -->
          <div
            v-if="products.length === 0"
            class="rounded border border-gray-200 px-6 py-20 text-center"
          >
            <h2 class="text-xl font-semibold">
              Your shopping cart is empty
            </h2>

            <p class="mt-3 text-sm text-gray-500">
              Discover something you'll love.
            </p>

            <button
              class="mt-6 bg-black px-8 py-3 text-sm text-white"
              @click="continueShopping"
            >
              Continue Shopping
            </button>
          </div>

          <!-- Product Cards -->
          <div
            v-for="item in products"
            :key="item.id"
            class="mb-[20px] flex min-h-[165px] gap-[21px] rounded-[4px] border border-[#E5E5E5] p-[17px]"
          >

            <!-- Image -->
            <div class="h-[130px] w-[122px] shrink-0 bg-[#F5F5F5]">
              <img
                :src="item.image"
                :alt="item.name"
                class="h-full w-full object-contain"
              />
            </div>

            <!-- Details -->
            <div class="min-w-0 flex-1">

              <div class="flex items-start justify-between gap-3">
                <h2 class="text-[18px] font-semibold">
                  {{ item.name }}
                </h2>

                <span class="whitespace-nowrap text-[16px] font-semibold">
                  {{ formatPrice(item.price * item.quantity) }}
                </span>
              </div>

              <p class="mt-[10px] text-[13px] text-[#888]">
                Color: {{ item.color }}
                &nbsp;·&nbsp;
                Size: {{ item.size }}
              </p>

              <!-- Quantity -->
              <div
                class="mt-[11px] flex h-[36px] w-[114px] items-center justify-between rounded border border-[#D6D6D6]"
              >
                <button
                  class="flex h-full w-[36px] items-center justify-center text-[16px] hover:bg-gray-100"
                  aria-label="Decrease quantity"
                  @click="decreaseQuantity(item)"
                >
                  −
                </button>

                <span class="text-[13px]">
                  {{ item.quantity }}
                </span>

                <button
                  class="flex h-full w-[36px] items-center justify-center text-[16px] hover:bg-gray-100"
                  aria-label="Increase quantity"
                  @click="increaseQuantity(item)"
                >
                  +
                </button>
              </div>

              <!-- Actions -->
              <div
                class="mt-[11px] flex items-center gap-[7px] text-[11px] text-[#929292]"
              >
                <button
                  class="hover:text-black"
                  @click="removeItem(item.id)"
                >
                  Remove
                </button>

                <span>·</span>

                <button
                  class="hover:text-black"
                  @click="moveToWishlist(item)"
                >
                  Move to Wishlist
                </button>
              </div>

            </div>
          </div>

          <!-- Continue Shopping -->
          <button
            class="mt-[1px] h-[45px] w-[190px] rounded border border-[#D5D5D5] text-[12px] font-medium transition hover:bg-gray-100"
            @click="continueShopping"
          >
            Continue Shopping
          </button>

          <p class="mt-[20px] text-[10px] text-[#999]">
            Quantity and item actions are design previews.
          </p>

        </div>

        <!-- RIGHT: Order Summary -->
        <div class="rounded-[5px] bg-[#F7F7F7] px-[20px] py-[22px]">

          <h2 class="mb-[21px] text-[22px] font-semibold">
            Order Summary
          </h2>

          <!-- Subtotal -->
          <div class="mb-[17px] flex justify-between text-[13px]">
            <span>Subtotal ({{ itemCount }} items)</span>
            <span>{{ formatPrice(subtotal) }}</span>
          </div>

          <!-- Shipping -->
          <div class="mb-[17px] flex justify-between text-[13px]">
            <span>Shipping</span>
            <span>{{ formatPrice(shipping) }}</span>
          </div>

          <!-- Tax -->
          <div class="mb-[20px] flex justify-between text-[13px]">
            <span>Tax</span>
            <span>At checkout</span>
          </div>

          <!-- Discount -->
          <div
            v-if="discount > 0"
            class="mb-[20px] flex justify-between text-[13px]"
          >
            <span>Discount</span>
            <span>-{{ formatPrice(discount) }}</span>
          </div>

          <div class="border-t border-[#DEDEDE]"></div>

          <!-- Total -->
          <div
            class="mt-[20px] flex items-center justify-between text-[13px] font-semibold"
          >
            <span>Estimated Total</span>
            <span>{{ formatPrice(total) }}</span>
          </div>

          <p class="mt-[20px] text-[11px] text-[#888]">
            Tax will be added at checkout.
          </p>

          <!-- Promo Code -->
          <div class="mt-[18px]">
            <label class="text-[13px]">
              Promo Code
            </label>

            <div
              class="mt-[18px] flex h-[40px] border border-[#D5D5D5] bg-white"
            >
              <input
                v-model="promoCode"
                type="text"
                placeholder="Enter promo code"
                class="min-w-0 flex-1 px-[12px] text-[12px] outline-none placeholder:text-[#999]"
                @keyup.enter="applyPromoCode"
              />

              <button
                class="px-[20px] text-[12px] font-medium hover:bg-gray-100"
                @click="applyPromoCode"
              >
                Apply
              </button>
            </div>

            <p
              v-if="promoMessage"
              class="mt-2 text-[11px] text-gray-600"
            >
              {{ promoMessage }}
            </p>
          </div>

          <!-- Checkout -->
          <button
            class="mt-[20px] flex h-[43px] w-full items-center justify-center rounded-[4px] bg-[#111] text-[12px] text-white transition hover:bg-[#333] disabled:cursor-not-allowed disabled:opacity-50"
            :disabled="products.length === 0"
            @click="proceedToCheckout"
          >
            Proceed to Checkout
            <span class="ml-[5px] text-[17px]">→</span>
          </button>

          <p class="mt-[20px] text-[10px] text-[#999]">
            Checkout button · Design preview
          </p>

          <!-- Shipping & Returns -->
          <h3 class="mt-[20px] text-[13px] font-medium">
            Shipping &amp; Returns
          </h3>

          <p class="mt-[18px] text-[12px] leading-[20px] text-[#888]">
            Review delivery and return details before checkout.
          </p>

        </div>
      </div>
    </div>
  </div>
</template>
