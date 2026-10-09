<script setup lang="ts">
const props = defineProps<{
  currentView?: string;
}>();
const emit = defineEmits<{
  (e: "navigate", view: string): void;
}>();
</script>

<template>
   <div class="w-full h-[30px] bg-[#fff8b7]"></div>
  <header class="relative h-[96px] w-full px-7">
    <!-- Search：左上 -->
    <div class="absolute left-7 top-3">
      <div class="relative">
        <input
          type="text"
          placeholder="Search..."
          class="w-[200px] h-[32px] pl-9 pr-4 rounded-lg border border-slate-300"
        />

        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="pointer-events-none absolute left-3 top-1/2 h-4 w-4 -translate-y-1/2 text-slate-500"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="m21 21-5.197-5.197m0 0A7.5 7.5 0 1 0 5.196 5.196a7.5 7.5 0 0 0 10.607 10.607Z"
          />
        </svg>
      </div>
    </div>

    <!-- Logo：正中間 -->
    <img
      src="/lala.png"
      alt="Logo"
      class="absolute left-1/2 top-3 h-[39px] w-[181px] -translate-x-1/2 object-contain"
    />

    <!-- Navigation：左下 -->
    <nav
      class="absolute bottom-3 left-7 hidden items-center gap-[40px] md:flex"
    >
      <a
        href="#"
        @click.prevent="emit('navigate', 'home')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'home'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Home
      </a>

      <a
        href="#"
        @click.prevent="emit('navigate', 'products')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'products'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Products
      </a>

      <a
        href="#"
        @click.prevent="emit('navigate', 'elements')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'elements'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Elements
      </a>

      <a
        href="#"
        @click.prevent="emit('navigate', 'pages')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'pages'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Pages
      </a>

      <a
        href="#"
        @click.prevent="emit('navigate', 'shop')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'shop'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Shop
      </a>

      <a
        href="#"
        @click.prevent="emit('navigate', 'sale')"
        :class="[
          'text-sm font-normal font-[Poppins]',
          props.currentView === 'sale'
            ? 'text-blue-500'
            : 'text-slate-700 hover:text-blue-500',
        ]"
      >
        Sale
      </a>
    </nav>

    <!-- Icons：右邊 -->
    <div
      class="absolute right-7 top-1/2 flex -translate-y-1/2 items-center gap-5"
    >
      <div>
        <form class="flex flex-col gap-4">
          <select id="size" class="border p-2">
            <option value="s">English</option>
            <option value="m">Chinese</option>
            <option value="l">Japanese</option>
          </select>
        </form>
      </div>

      <div>
        <form class="flex flex-col gap-4">
          <select id="size" class="border p-2">
            <option value="s">USD</option>
            <option value="m">NTD</option>
            <option value="l">JPY</option>
          </select>
        </form>
      </div>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="h-6 w-6 text-slate-700"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12Z"
        />
      </svg>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="h-6 w-6 text-slate-700"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M14.857 17.082a23.848 23.848 0 0 0 5.454-1.31A8.967 8.967 0 0 1 18 9.75V9A6 6 0 0 0 6 9v.75a8.967 8.967 0 0 1-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 0 1-5.714 0m5.714 0a3 3 0 1 1-5.714 0"
        />
      </svg>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="h-6 w-6 text-slate-700"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 0 0-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 0 0-16.536-1.84M7.5 14.25 5.106 5.272M6 20.25a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0Zm12.75 0a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0Z"
        />
      </svg>
<!-- Profile -->
      <button
        @click.prevent="emit('navigate', 'profile')"
        class="h-6 w-6 text-slate-700">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="size-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M17.982 18.725A7.488 7.488 0 0 0 12 15.75a7.488 7.488 0 0 0-5.982 2.975m11.963 0a9 9 0 1 0-11.963 0m11.963 0A8.966 8.966 0 0 1 12 21a8.966 8.966 0 0 1-5.982-2.275M15 9.75a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
        />
      </svg>
      </button>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="size-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M10.343 3.94c.09-.542.56-.94 1.11-.94h1.093c.55 0 1.02.398 1.11.94l.149.894c.07.424.384.764.78.93.398.164.855.142 1.205-.108l.737-.527a1.125 1.125 0 0 1 1.45.12l.773.774c.39.389.44 1.002.12 1.45l-.527.737c-.25.35-.272.806-.107 1.204.165.397.505.71.93.78l.893.15c.543.09.94.559.94 1.109v1.094c0 .55-.397 1.02-.94 1.11l-.894.149c-.424.07-.764.383-.929.78-.165.398-.143.854.107 1.204l.527.738c.32.447.269 1.06-.12 1.45l-.774.773a1.125 1.125 0 0 1-1.449.12l-.738-.527c-.35-.25-.806-.272-1.203-.107-.398.165-.71.505-.781.929l-.149.894c-.09.542-.56.94-1.11.94h-1.094c-.55 0-1.019-.398-1.11-.94l-.148-.894c-.071-.424-.384-.764-.781-.93-.398-.164-.854-.142-1.204.108l-.738.527c-.447.32-1.06.269-1.45-.12l-.773-.774a1.125 1.125 0 0 1-.12-1.45l.527-.737c.25-.35.272-.806.108-1.204-.165-.397-.506-.71-.93-.78l-.894-.15c-.542-.09-.94-.56-.94-1.109v-1.094c0-.55.398-1.02.94-1.11l.894-.149c.424-.07.765-.383.93-.78.165-.398.143-.854-.108-1.204l-.526-.738a1.125 1.125 0 0 1 .12-1.45l.773-.773a1.125 1.125 0 0 1 1.45-.12l.737.527c.35.25.807.272 1.204.107.397-.165.71-.505.78-.929l.15-.894Z"
        />
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
        />
      </svg>
    </div>
  </header>
 
</template>
