<script setup lang="ts">
import { ref } from "vue";

const activeTab = ref("signin");
const email = ref("");
const password = ref("");

function signIn() {
  if (email.value === "" || password.value === "") {
    alert("Please enter your email and password");
    return;
  }

  alert("Sign in clicked");
}
</script>

<template>
  <main class="w-full min-h-screen bg-white text-black">
    <!-- PAGE TITLE -->
    <div class="text-center pt-[60px]">
      <h1 class="text-[28px] font-bold">SIGN IN</h1>

      <p class="text-[14px] text-gray-400 mt-4">Sign in or create an account</p>
    </div>

    <!-- SIGN IN / SIGN UP TABS -->
    <div class="flex w-[400px] mx-auto mt-6 border-b-2 border-gray-400">
      <button
        @click="activeTab = 'signin'"
        class="w-1/2 py-2 text-[14px]"
        :class="activeTab === 'signin' ? 'border-b-2 border-black' : ''"
      >
        Sign in
      </button>

      <button
        @click="activeTab = 'signup'"
        class="w-1/2 py-2 text-[14px]"
        :class="activeTab === 'signup' ? 'border-b-2 border-black' : ''"
      >
        Sign up
      </button>
    </div>

    <!-- LOGIN AREA -->
    <div class="flex justify-center items-start gap-[60px] mt-[45px]">
      <!-- LEFT SIDE -->
      <div class="w-[363px]">
        <form @submit.prevent="signIn">
          <!-- EMAIL -->
          <input
            v-model="email"
            type="text"
            placeholder="User ID or Email"
            class="w-full border-b border-gray-600 py-3 text-[14px] outline-none placeholder:text-gray-400"
          />

          <!-- PASSWORD -->
          <input
            v-model="password"
            type="password"
            placeholder="Password"
            class="w-full border-b border-gray-600 py-3 mt-[25px] text-[14px] outline-none placeholder:text-gray-400"
          />

          <!-- FORGOT PASSWORD -->
          <div class="flex justify-between mt-8 text-[12px]">
            <a href="#" class="hover:underline"> Forgot ID or password? </a>

            <a href="#" class="underline"> Find account </a>
          </div>

          <!-- SIGN IN BUTTON -->
          <button
            type="submit"
            class="w-full h-[44px] bg-black text-white text-[14px] mt-4 hover:bg-gray-800"
          >
            {{ activeTab === "signin" ? "Sign In" : "Sign Up" }}
          </button>
        </form>
      </div>

      <!-- OR -->
      <div class="text-[16px] mt-[55px]">Or</div>

      <!-- RIGHT SIDE -->
      <div class="w-[328px] flex flex-col gap-[18px] pt-[8px]">
        <!-- FACEBOOK -->
        <button
          class="flex items-center gap-3 w-full h-[47px] border border-gray-600 px-4 text-[12px] hover:bg-gray-50"
        >
          <img
            src="https://www.svgrepo.com/show/448224/facebook.svg"
            alt="Facebook"
            class="w-[28px] h-[28px]"
          />

          Continue with Facebook
        </button>

        <!-- GOOGLE -->

        <!-- GOOGLE -->
        <button
          class="flex items-center gap-3 w-full h-[47px] border border-gray-600 px-4 text-[12px] hover:bg-gray-50"
        >
          <img
            src="https://www.svgrepo.com/show/475656/google-color.svg"
            alt="Google"
            class="w-[28px] h-[28px]"
          />

          Continue with Google
        </button>
      </div>
    </div>
  </main>
</template>
