<script setup lang="ts">
import { ref, computed } from "vue";
import ProductCard from "../components/ProductCard.vue";

const products = [
  {
    id: 1,
    name: "Cotton Oversized Tee",
    price: 40,
    rating: 4.7,
    reviews: 3,
    category: "Tops & Shirts",
    sizes: ["XS", "S", "M", "L", "XL"],
    colors: ["White", "Neutral", "Black"],
    image: "/product1.jpg",
  },
  {
    id: 2,
    name: "Everyday Knit Sweater",
    price: 68,
    rating: 4.8,
    reviews: 12,
    category: "Knitwear",
    sizes: ["S", "M", "L"],
    colors: ["Neutral", "White", "Black"],
    image: "/product2.jpg",
  },
  {
    id: 3,
    name: "Pleated Midi Skirt",
    price: 56,
    rating: 4.5,
    reviews: 8,
    category: "Skirts",
    sizes: ["XS", "S", "M", "L"],
    colors: ["Black", "Neutral"],
    image: "/product3.jpg",
  },
  {
    id: 4,
    name: "Relaxed Cotton Shirt",
    price: 62,
    rating: 4.6,
    reviews: 15,
    category: "Tops & Shirts",
    sizes: ["XS", "S", "M", "L", "XL"],
    colors: ["Blue", "White"],
    image: "/product4.jpg",
  },
  {
    id: 5,
    name: "Wide Leg Trousers",
    price: 74,
    rating: 4.7,
    reviews: 9,
    category: "Trousers",
    sizes: ["S", "M", "L", "XL"],
    colors: ["Neutral", "Black"],
    image: "/product5.jpg",
  },
  {
    id: 6,
    name: "Essential Black Tee",
    price: 35,
    rating: 4.9,
    reviews: 21,
    category: "Tops & Shirts",
    sizes: ["XS", "S", "M", "L", "XL"],
    colors: ["Black", "White", "Neutral"],
    image: "/product6.jpg",
  },
];

const categories = [
  "All Clothing",
  "Tops & Shirts",
  "Knitwear",
  "Skirts",
  "Trousers",
];

const sizes = ["XS", "S", "M", "L", "XL"];

const colorOptions = [
  { name: "White", hex: "#ffffff" },
  { name: "Black", hex: "#242424" },
  { name: "Neutral", hex: "#b9b09f" },
  { name: "Blue", hex: "#b8cbd5" },
];

const selectedCategory = ref("All Clothing");
const selectedSizes = ref<string[]>([]);
const selectedRatings = ref<number[]>([]);
const selectedColors = ref<string[]>([]);
const minPrice = ref(0);
const maxPrice = ref(150);
const sortBy = ref("featured");

// FILTER PRODUCTS
const filteredProducts = computed(() => {
  let result = products.filter((product) => {
    const categoryMatch =
      selectedCategory.value === "All Clothing" ||
      product.category === selectedCategory.value;

    const sizeMatch =
      selectedSizes.value.length === 0 ||
      selectedSizes.value.some((size) => product.sizes.includes(size));

    const priceMatch =
      product.price >= minPrice.value && product.price <= maxPrice.value;

    const ratingMatch =
      selectedRatings.value.length === 0 ||
      selectedRatings.value.some((rating) => product.rating >= rating);

    const colorMatch =
      selectedColors.value.length === 0 ||
      selectedColors.value.some((color) => product.colors.includes(color));

    return (
      categoryMatch && sizeMatch && priceMatch && ratingMatch && colorMatch
    );
  });

  if (sortBy.value === "low") {
    result = [...result].sort((a, b) => a.price - b.price);
  }

  if (sortBy.value === "high") {
    result = [...result].sort((a, b) => b.price - a.price);
  }

  if (sortBy.value === "rating") {
    result = [...result].sort((a, b) => b.rating - a.rating);
  }

  if (sortBy.value === "name") {
    result = [...result].sort((a, b) => a.name.localeCompare(b.name));
  }

  return result;
});

// CATEGORY COUNT
function categoryCount(category: string) {
  if (category === "All Clothing") return products.length;
  return products.filter((product) => product.category === category).length;
}

// SIZE
function toggleSize(size: string) {
  if (selectedSizes.value.includes(size)) {
    selectedSizes.value = selectedSizes.value.filter((item) => item !== size);
  } else {
    selectedSizes.value.push(size);
  }
}

// RATING
function toggleRating(rating: number) {
  if (selectedRatings.value.includes(rating)) {
    selectedRatings.value = selectedRatings.value.filter(
      (item) => item !== rating,
    );
  } else {
    selectedRatings.value.push(rating);
  }
}

// COLOR
function toggleColor(color: string) {
  if (selectedColors.value.includes(color)) {
    selectedColors.value = selectedColors.value.filter(
      (item) => item !== color,
    );
  } else {
    selectedColors.value.push(color);
  }
}

// RESET FILTERS
function resetFilters() {
  selectedCategory.value = "All Clothing";
  selectedSizes.value = [];
  selectedRatings.value = [];
  selectedColors.value = [];
  minPrice.value = 0;
  maxPrice.value = 150;
  sortBy.value = "featured";
}

// PRICE RANGE
function setMinPrice(value: number) {
  minPrice.value = Math.max(0, Math.min(value || 0, maxPrice.value));
}

function setMaxPrice(value: number) {
  maxPrice.value = Math.min(150, Math.max(value || 0, minPrice.value));
}
</script>

<template>
  <main class="w-full bg-white text-[#202020] min-h-screen">
    <div class="w-full px-5 md:px-10 pt-[50px] pb-[80px]">
      <!-- PAGE HEADER -->
      <div class="mb-[48px]">
        <p class="text-[11px] text-gray-400 uppercase tracking-[2px] mb-3">
          THE EVERYDAY EDIT
        </p>

        <h1 class="text-[40px] font-semibold leading-tight">
          Find your next favorite.
        </h1>

        <p class="text-[15px] text-gray-500 mt-4">
          Easy layers. Thoughtful details. Made for your everyday.
        </p>
      </div>

      <!-- MAIN LAYOUT -->
      <div class="flex gap-[44px] items-start">
        <!-- LEFT SIDEBAR -->
        <aside class="w-[200px] shrink-0">
          <!-- FILTER HEADER -->
          <div class="flex justify-between items-center mb-6">
            <h2 class="text-[18px] font-semibold">Filters</h2>

            <button
              @click="resetFilters"
              class="text-[12px] text-gray-400 hover:text-black"
            >
              Reset
            </button>
          </div>

          <!-- CATEGORY -->
          <div class="border-b border-gray-200 pb-6 mb-6">
            <h3 class="text-[13px] font-semibold mb-3">Category</h3>

            <div class="flex flex-col gap-2">
              <button
                v-for="category in categories"
                :key="category"
                @click="selectedCategory = category"
                class="flex items-center gap-2 w-full px-2 py-2 text-left text-[12px]"
                :class="
                  selectedCategory === category
                    ? 'bg-[#f3f3f3] font-medium'
                    : 'hover:bg-gray-50'
                "
              >
                <span
                  class="w-[11px] h-[11px] rounded-full border border-gray-400 shrink-0"
                  :class="
                    selectedCategory === category
                      ? 'bg-[#222] border-[#222]'
                      : 'bg-white'
                  "
                ></span>

                <span>{{ category }}</span>

                <span class="text-gray-400">
                  {{ categoryCount(category) }}
                </span>
              </button>
            </div>
          </div>

          <!-- SIZE -->
          <div class="border-b border-gray-200 pb-6 mb-6">
            <h3 class="text-[13px] font-semibold mb-3">Size</h3>

            <div class="grid grid-cols-3 gap-2">
              <button
                v-for="size in sizes"
                :key="size"
                @click="toggleSize(size)"
                class="h-[35px] border rounded-[3px] text-[12px] transition"
                :class="
                  selectedSizes.includes(size)
                    ? 'bg-black text-white border-black'
                    : 'border-gray-300 hover:border-black'
                "
              >
                {{ size }}
              </button>
            </div>
          </div>

          <!-- PRICE RANGE -->
          <div class="border-b border-gray-200 pb-6 mb-6">
            <h3 class="text-[13px] font-semibold mb-4">Price Range</h3>

            <div class="relative mb-5 pt-2">
              <div class="h-[2px] bg-gray-200"></div>

              <div
                class="absolute h-[2px] bg-[#222] top-2"
                :style="{
                  left: (minPrice / 150) * 100 + '%',
                  right: 100 - (maxPrice / 150) * 100 + '%',
                }"
              ></div>

              <input
                type="range"
                min="0"
                max="150"
                step="1"
                :value="minPrice"
                @input="
                  setMinPrice(Number(($event.target as HTMLInputElement).value))
                "
                aria-label="Minimum price"
                class="price-slider absolute w-full left-0 top-0"
              />

              <input
                type="range"
                min="0"
                max="150"
                step="1"
                :value="maxPrice"
                @input="
                  setMaxPrice(Number(($event.target as HTMLInputElement).value))
                "
                aria-label="Maximum price"
                class="price-slider absolute w-full left-0 top-0"
              />
            </div>

            <div class="flex gap-3">
              <div
                class="flex-1 min-w-0 border border-gray-300 rounded-[3px] px-2 py-2 text-[12px]"
              >
                ${{ minPrice }}
              </div>

              <div
                class="flex-1 min-w-0 border border-gray-300 rounded-[3px] px-2 py-2 text-[12px]"
              >
                ${{ maxPrice }}
              </div>
            </div>
          </div>

          <!-- RATING -->
          <div class="border-b border-gray-200 pb-6 mb-6">
            <h3 class="text-[13px] font-semibold mb-3">Rating</h3>

            <div class="flex flex-col gap-3">
              <label
                v-for="rating in [4, 3, 2]"
                :key="rating"
                class="flex items-center gap-2 cursor-pointer text-[12px]"
              >
                <input
                  type="checkbox"
                  :checked="selectedRatings.includes(rating)"
                  @change="toggleRating(rating)"
                  class="w-[12px] h-[12px] accent-black"
                />

                <span>
                  <span class="text-black">{{ "★".repeat(rating) }}</span
                  ><span class="text-gray-400">{{
                    "☆".repeat(5 - rating)
                  }}</span>
                  & up
                </span>
              </label>
            </div>
          </div>

          <!-- COLOR -->
          <div>
            <h3 class="text-[13px] font-semibold mb-3">Color</h3>

            <div class="flex flex-col gap-3">
              <button
                v-for="color in colorOptions"
                :key="color.name"
                @click="toggleColor(color.name)"
                class="flex items-center gap-3 text-[12px] text-left"
              >
                <span
                  class="w-[18px] h-[18px] rounded-full border border-gray-300"
                  :style="{ backgroundColor: color.hex }"
                  :class="
                    selectedColors.includes(color.name)
                      ? 'ring-2 ring-offset-2 ring-black'
                      : ''
                  "
                ></span>

                {{ color.name }}
              </button>
            </div>
          </div>

          <p class="text-[10px] text-gray-400 mt-6">
            Filter controls · Design preview
          </p>
        </aside>

        <!-- RIGHT PRODUCT AREA -->
        <section class="flex-1 min-w-0">
          <!-- PRODUCT COUNT AND SORT -->
          <div class="flex items-center justify-between mb-5">
            <p class="text-[13px]">{{ filteredProducts.length }} products</p>

            <div class="flex items-center gap-1 text-[13px]">
              <span>Sort:</span>

              <select
                v-model="sortBy"
                class="bg-transparent outline-none cursor-pointer text-[13px]"
              >
                <option value="featured">Featured</option>
                <option value="low">Price: Low to High</option>
                <option value="high">Price: High to Low</option>
                <option value="rating">Top Rated</option>
                <option value="name">Name: A to Z</option>
              </select>
            </div>
          </div>

          <!-- PRODUCT GRID -->
          <div class="grid grid-cols-3 gap-x-6 gap-y-6">
            <ProductCard
              v-for="product in filteredProducts"
              :key="product.id"
              :title="product.name"
              :image="product.image"
              :price="product.price"
              :rating="product.rating"
              :reviews="product.reviews"
              :colors="
                product.colors.map(
                  (color) =>
                    colorOptions.find((c) => c.name === color)?.hex ||
                    '#ffffff',
                )
              "
            />
          </div>

          <!-- EMPTY STATE -->
          <div
            v-if="filteredProducts.length === 0"
            class="py-[100px] text-center"
          >
            <h3 class="text-[20px] font-medium">No products found</h3>

            <p class="text-gray-400 text-[14px] mt-3">
              Try changing your filters.
            </p>

            <button
              @click="resetFilters"
              class="mt-6 border border-black px-6 py-3 text-[13px]"
            >
              Reset filters
            </button>
          </div>

          <p class="text-[11px] text-gray-400 mt-5">
            Ratings shown are sample data.
          </p>
        </section>
      </div>
    </div>
  </main>
</template>

<style scoped>
.price-slider {
  appearance: none;
  -webkit-appearance: none;
  background: transparent;
  pointer-events: none;
  height: 16px;
  margin: 0;
}

.price-slider::-webkit-slider-thumb {
  appearance: none;
  -webkit-appearance: none;
  width: 14px;
  height: 14px;
  background: white;
  border: 2px solid #222;
  border-radius: 50%;
  cursor: pointer;
  pointer-events: auto;
}

.price-slider::-moz-range-thumb {
  width: 11px;
  height: 11px;
  background: white;
  border: 2px solid #222;
  border-radius: 50%;
  cursor: pointer;
  pointer-events: auto;
}
</style>
