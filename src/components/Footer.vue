<script setup lang="ts">
const emit = defineEmits<{
  (e: "navigate", view: string): void;
}>();

const footerGroups = [
  {
    title: "Explore",
    links: [
      { label: "Home", view: "home" },
      { label: "Products", view: "products" },
      { label: "About Us", view: "about" },
    ],
  },
  {
    title: "Your Account",
    links: [
      { label: "My Account", view: "profile" },
      { label: "Sign In", view: "signin" },
      { label: "Sign Up", view: "signup" },
    ],
  },
];
</script>

<template>
  <footer class="w-full bg-black px-6 py-12 text-white md:px-12 lg:px-[70px]">
    <div class="mx-auto max-w-[1440px]">
      <!-- Brand and newsletter -->
      <div
        class="flex flex-col gap-8 border-b border-white/35 pb-10 lg:flex-row lg:items-center lg:justify-between"
      >
        <div>
          <img
            src="/logo.png"
            alt="Aifos"
            class="h-[44px] w-[181px] object-contain object-left brightness-0 invert"
          />

          <p class="mt-4 text-sm text-white/85">
            Everyday pieces. A little more you.
          </p>
        </div>

        <div class="w-full lg:max-w-[520px]">
          <h2 class="text-lg font-medium">Stay in the loop.</h2>

          <p class="mt-2 text-sm text-white/85">
            Discover new collections and everyday inspiration.
          </p>

          <!-- Connect to a newsletter service to enable signup -->
          <div class="mt-5 flex border-b border-white/70 focus-within:border-white">
            <input
              type="email"
              aria-label="Email address"
              placeholder="Your email address"
              class="h-12 min-w-0 flex-1 border-0 bg-transparent pr-4 text-sm text-white outline-none placeholder:text-white/65"
            />

            <button
              type="button"
              disabled
              title="Newsletter signup coming soon"
              class="shrink-0 cursor-default px-2 text-sm text-white/75"
            >
              Subscribe ↗
            </button>
          </div>
        </div>
      </div>

      <!-- Navigation -->
      <div class="grid grid-cols-2 gap-x-8 gap-y-10 py-10 md:grid-cols-4">
        <div
          v-for="group in footerGroups"
          :key="group.title"
        >
          <h2 class="mb-5 text-sm font-semibold">
            {{ group.title }}
          </h2>

          <div class="flex flex-col items-start gap-3">
            <button
              v-for="link in group.links"
              :key="link.view"
              type="button"
              @click="emit('navigate', link.view)"
              class="text-left text-sm text-white/85 transition hover:text-white"
            >
              {{ link.label }}
            </button>
          </div>
        </div>

        <div>
          <h2 class="mb-5 text-sm font-semibold">Customer Care</h2>

          <div class="flex flex-col gap-3 text-sm text-white/85">
            <p>Orders & Tracking</p>
            <p>Shipping & Delivery</p>
            <p>Returns & Refunds</p>
          </div>
        </div>

        <div>
          <h2 class="mb-5 text-sm font-semibold">Made to go with you.</h2>

          <p class="max-w-[260px] text-sm leading-7 text-white/85">
            From everyday essentials to expressive details,
            find something that feels like you.
          </p>

          <button
            type="button"
            @click="emit('navigate', 'products')"
            class="mt-5 border-b border-white/75 pb-1 text-sm transition hover:border-white"
          >
            Explore the collection ↗
          </button>
        </div>
      </div>

      <!-- Bottom -->
      <div
        class="flex flex-col gap-4 border-t border-white/35 pt-6 text-xs text-white/75 sm:flex-row sm:items-center sm:justify-between"
      >
        <p>© 2026 Aifos. All rights reserved.</p>
        <p>Everyday, your way.</p>
      </div>
    </div>
  </footer>
</template>