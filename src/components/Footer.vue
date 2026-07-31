<script setup>
</script>

<template>
  <div class="bg-[#A6A6A6] max-w-[1440px] h-[578px] p-4 mx-auto">
    <div class="mx-auto max-w-[1100px]">
      <div class="flex items-center justify-between">
        <img src="/lala.png" alt="Logo" class="w-[181px] h-[39px]" />
        <div class="flex items-center gap-4">
          <div class="relative">
            <input
              type="text"
              placeholder="Enter your email to get latest news..."
              class="w-[497px] h-[48px] pl-12 pr-4 rounded-lg border border-slate-300"
            />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="pointer-events-none absolute left-3 top-1/2 h-5 w-5 -translate-y-1/2 text-slate-500"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M21.75 6.75v10.5a2.25 2.25 0 0 1-2.25 2.25h-15a2.25 2.25 0 0 1-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25m19.5 0v.243a2.25 2.25 0 0 1-1.07 1.916l-7.5 4.615a2.25 2.25 0 0 1-2.36 0L3.32 8.91a2.25 2.25 0 0 1-1.07-1.916V6.75"
              />
            </svg>
          </div>
          <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Subscribe
          </button>
        </div>
      </div>

      <div class="grid w-full grid-cols-2 gap-[80px] mt-[50px] md:grid-cols-4 justify-items-center">
        <div class="font-bold flex flex-col gap-[20px]">
          <h1>About Us</h1>
          <p>Brand Protection</p>
          <p>Careers</p>
          <p>Accessibilities</p>
        </div>

        <div class="font-bold flex flex-col gap-[20px]">
          <h1>Help</h1>
          <p>Customer Help</p>
          <p>Order Help</p>
          <p>Shipping and Handling</p>
        </div>

        <div class="font-bold flex flex-col gap-[20px]">
          <h1>Resources</h1>
          <p>Blog</p>
          <p>FAQ</p>
          <p>Contact</p>
        </div>

        <div>
          <div class="font-bold flex flex-row gap-[20px]">
            <button class="bg-[#000000] hover:bg-[#020000] text-white font-bold py-2 px-4 rounded">
              Download On Apple Store
            </button>
            <button class="bg-[#000000] hover:bg-[#000000] text-white font-bold py-2 px-4 rounded">
              Like us on Google Play
            </button>
          </div>
          <h1 class="mt-4">Join Us</h1>
        </div>
      </div>
    </div>
  </div>
</template>
