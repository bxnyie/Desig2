<script setup></script>

<template>
  <div
    class="bg-[#747B82] max-w-[1440px] min-h-[500px] px-[70px] py-[45px] mx-auto"
  >
    <div class="mx-auto max-w-[1100px]">
      <!-- Top -->
      <div
        class="flex items-center justify-between border-b border-white/30 pb-[35px]"
      >
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

          <button
            class="h-[48px] bg-blue-500 hover:bg-blue-700 text-white font-bold px-5 rounded"
          >
            Subscribe
          </button>
        </div>
      </div>

      <!-- Middle -->
      <div
        class="grid w-full grid-cols-2 gap-[70px] mt-[45px] md:grid-cols-4 items-start"
      >
        <div class="flex flex-col gap-[14px] text-white">
          <h1 class="font-bold mb-1">About Us</h1>
          <p class="text-sm">Brand Protection</p>
          <p class="text-sm">Careers</p>
          <p class="text-sm">Accessibilities</p>
        </div>

        <div class="flex flex-col gap-[14px] text-white">
          <h1 class="font-bold mb-1">Help</h1>
          <p class="text-sm">Customer Help</p>
          <p class="text-sm">Order Help</p>
          <p class="text-sm whitespace-nowrap">Shipping and Handling</p>
        </div>

        <div class="flex flex-col gap-[14px] text-white">
          <h1 class="font-bold mb-1">Resources</h1>
          <p class="text-sm">Blog</p>
          <p class="text-sm">FAQ</p>
          <p class="text-sm">Contact</p>
        </div>

        <div class="text-white">
          <h1 class="font-bold mb-4">Download</h1>

          <div class="flex flex-row gap-[8px]">
            <!-- Apple Store -->
            <button
              class="w-[150px] h-[50px] bg-black hover:bg-[#111] text-white rounded-[5px] px-3 flex items-center gap-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="w-[28px] h-[28px] shrink-0"
                viewBox="0 0 24 24"
                fill="none"
              >
                <path
                  d="M16 2C16.3632 4.17921 14.0879 5.83084 12.8158 6.57142C12.4406 6.78988 12.0172 6.5117 12.0819 6.08234C12.2993 4.63878 13.0941 2.00008 16 2Z"
                  stroke="white"
                  stroke-width="1.5"
                />
                <path
                  d="M9 6.5C9.89676 6.5 10.6905 6.69941 11.2945 6.92013C12.0563 7.19855 12.9437 7.19854 13.7055 6.92012C14.3094 6.6994 15.1032 6.5 15.9999 6.5C17.0852 6.5 18.4649 7.08889 19.4999 8.26666C16 11 17 15.5 20.269 16.6916C19.2253 19.5592 17.2413 21.5 15.4999 21.5C13.9999 21.5 14 20.8 12.5 20.8C11 20.8 11 21.5 9.5 21.5C7 21.5 4 17.5 4 12.5C4 8.5 7 6.5 9 6.5Z"
                  stroke="white"
                  stroke-width="1.5"
                />
              </svg>

              <div
                class="flex flex-col items-start text-left whitespace-nowrap"
              >
                <span class="text-[9px] leading-[11px] font-normal">
                  Download on the
                </span>

                <span class="text-[20px] leading-[22px] font-normal">
                  App Store
                </span>
              </div>
            </button>

            <!-- Google Play -->
            <button
              class="w-[150px] h-[50px] bg-black hover:bg-[#111] text-white rounded-[5px] px-3 flex items-center gap-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="w-[28px] h-[28px] shrink-0"
                viewBox="0 0 24 24"
                fill="none"
              >
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M12 4.15039C10.8087 4.15039 9.42076 4.17798 8.06649 4.21628L8.01146 4.21784C6.63265 4.25681 5.52112 4.28823 4.64461 4.43318C3.73199 4.58411 2.97386 4.87211 2.36772 5.49563C1.75996 6.12082 1.49451 6.89404 1.3699 7.81907C1.24996 8.70944 1.24998 9.83697 1.25 11.2382V12.7627C1.24998 14.1639 1.24996 15.2914 1.3699 16.1818C1.4945 17.1068 1.75996 17.88 2.36771 18.5052C2.97384 19.1287 3.73195 19.4167 4.64456 19.5676C5.52106 19.7126 6.63258 19.744 8.01137 19.783L8.06639 19.7846C9.42068 19.8229 10.8087 19.8505 12 19.8505C13.1913 19.8505 14.5793 19.8229 15.9336 19.7846L15.9886 19.783C17.3674 19.744 18.4789 19.7126 19.3554 19.5676C20.2681 19.4167 21.0262 19.1287 21.6323 18.5052C22.24 17.88 22.5055 17.1068 22.6301 16.1818C22.75 15.2914 22.75 14.1639 22.75 12.7627V11.2381C22.75 9.83696 22.75 8.70944 22.6301 7.81907C22.5055 6.89404 22.24 6.12082 21.6323 5.49563C21.0261 4.87211 20.268 4.58411 19.3554 4.43318C18.4789 4.28823 17.3674 4.25681 15.9885 4.21784L15.9335 4.21628C14.5792 4.17798 13.1913 4.15039 12 4.15039ZM10.8721 14.6512C10.64 14.7838 10.3548 14.7829 10.1236 14.6487C9.89232 14.5145 9.75 14.2674 9.75 14V10C9.75 9.73265 9.89232 9.48551 10.1236 9.35132C10.3548 9.21713 10.64 9.21617 10.8721 9.34882L14.3721 11.3488C14.6058 11.4823 14.75 11.7309 14.75 12C14.75 12.2691 14.6058 12.5177 14.3721 12.6512L10.8721 14.6512Z"
                  fill="white"
                />
              </svg>

              <div
                class="flex flex-col items-start text-left whitespace-nowrap"
              >
                <span class="text-[9px] leading-[11px] font-normal">
                  Get it on
                </span>

                <span class="text-[18px] leading-[21px] font-normal">
                  Google Play
                </span>
              </div>
            </button>
          </div>

          <h1 class="mt-5 mb-3 font-bold">Join Us</h1>

          <div class="flex items-center gap-4">
            <!-- YouTube -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 h-5"
              viewBox="0 0 24 24"
              fill="white"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M12 4.15039C10.8087 4.15039 9.42076 4.17798 8.06649 4.21628L8.01146 4.21784C6.63265 4.25681 5.52112 4.28823 4.64461 4.43318C3.73199 4.58411 2.97386 4.87211 2.36772 5.49563C1.75996 6.12082 1.49451 6.89404 1.3699 7.81907C1.24996 8.70944 1.24998 9.83697 1.25 11.2382V12.7627C1.24998 14.1639 1.24996 15.2914 1.3699 16.1818C1.4945 17.1068 1.75996 17.88 2.36771 18.5052C2.97384 19.1287 3.73195 19.4167 4.64456 19.5676C5.52106 19.7126 6.63258 19.744 8.01137 19.783L8.06639 19.7846C9.42068 19.8229 10.8087 19.8505 12 19.8505C13.1913 19.8505 14.5793 19.8229 15.9336 19.7846L15.9886 19.783C17.3674 19.744 18.4789 19.7126 19.3554 19.5676C20.2681 19.4167 21.0262 19.1287 21.6323 18.5052C22.24 17.88 22.5055 17.1068 22.6301 16.1818C22.75 15.2914 22.75 14.1639 22.75 12.7627V11.2381C22.75 9.83696 22.75 8.70944 22.6301 7.81907C22.5055 6.89404 22.24 6.12082 21.6323 5.49563C21.0261 4.87211 20.268 4.58411 19.3554 4.43318C18.4789 4.28823 17.3674 4.25681 15.9885 4.21784L15.9335 4.21628C14.5792 4.17798 13.1913 4.15039 12 4.15039ZM10.8721 14.6512C10.64 14.7838 10.3548 14.7829 10.1236 14.6487C9.89232 14.5145 9.75 14.2674 9.75 14V10C9.75 9.73265 9.89232 9.48551 10.1236 9.35132C10.3548 9.21713 10.64 9.21617 10.8721 9.34882L14.3721 11.3488C14.6058 11.4823 14.75 11.7309 14.75 12C14.75 12.2691 14.6058 12.5177 14.3721 12.6512L10.8721 14.6512Z"
              />
            </svg>

            <span class="text-sm font-bold">f</span>
            <span class="text-sm font-bold">♥</span>
            <span class="text-sm font-bold">◎</span>
            <span class="text-sm font-bold">in</span>
          </div>
        </div>
      </div>

      <!-- Bottom -->
      <div
        class="mt-[45px] border-t border-white/30 pt-[30px] flex justify-between text-white text-sm"
      >
        <p>Aifos @ 2026. All rights reserved.</p>

        <div class="flex gap-6">
          <span>Home</span>
          <span>About Us</span>
          <span>Help</span>
        </div>
      </div>
    </div>
  </div>
</template>
