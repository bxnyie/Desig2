<script setup>
import { ref } from "vue";
</script>


 
<template>
  <div class="flex gap-10 p-8">

    <!-- LEFT: My Account -->
   <div class="w-[250px]">

  <p class="text-sm text-gray-500">
    MY ACCOUNT
  </p>

  <h1 class="text-3xl font-bold mt-4 mb-5">
    My Account
  </h1>

  <div class="p-4 bg-gray-100 hover:bg-gray-200 cursor-pointer">
    User Details
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Past Orders
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Login and Security
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Payment Methods
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Address Book
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Notifications
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Privacy Settings
  </div>

  <div class="p-4 hover:bg-gray-100 cursor-pointer">
    Delete Account
  </div>

  <div class="p-4 mt-4 text-gray-500 hover:bg-gray-100 cursor-pointer">
    Logout
  </div>

</div>


    <!-- RIGHT: My Profile -->
    <div class="w-[900px]">

      <h1 class="text-3xl font-bold mb-6">
        My Profile
      </h1>

      <p class="text-gray-500 mb-7">
        Manage your personal details and delivery information.
      </p>

      <!-- Profile Photo -->
      <div class="flex items-center gap-6 mb-7">

        <div class="w-20 h-20 rounded-full bg-gray-100">
        </div>

        <div>
          <p class="font-medium">
            Profile photo
          </p>

          <p class="font-semibold mt-2">
            Upload Photo
          </p>

          <p class="text-sm text-gray-500 mt-1">
            JPG or PNG · Maximum file size: 1 MB
          </p>
        </div>

      </div>

      <hr class="mb-8" />

      <!-- Personal Information -->
      <h2 class="text-xl font-semibold mb-7">
        Personal Information
      </h2>

      <div class="grid grid-cols-2 gap-8">

        <!-- First Name -->
        <div>
          <p class="mb-2">First Name</p>
          <input
            type="text"
            placeholder="Enter first name"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

        <!-- Last Name -->
        <div>
          <p class="mb-2">Last Name</p>
          <input
            type="text"
            placeholder="Enter last name"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

        <!-- Email Address -->
        <div>
          <p class="mb-2">Email Address</p>
          <input
            type="text"
            placeholder="name@example.com"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

        <!-- Phone Number -->
        <div>
          <p class="mb-2">Phone Number</p>
          <input
            type="text"
            placeholder="Enter phone number"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

        <!-- Date of Birth -->
        <div>
          <p class="mb-2">Date of Birth (optional)</p>
          <input
            type="text"
            placeholder="MM / DD / YYYY"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

        <!-- Country -->
        <div>
          <p class="mb-2">Country / Region</p>
          <input
            type="text"
            placeholder="United States"
            class="w-full border border-gray-300 rounded p-4"
          />
        </div>

      </div>

      <hr class="my-8" />

      <!-- Saved Address -->
      <div class="flex items-center gap-8 mb-7">

        <h2 class="text-xl font-semibold">
          Saved Address
        </h2>

        <p>
          + Add New Address
        </p>

      </div>

      <div class="bg-gray-100 p-6 mb-7">

        <p class="text-xs text-gray-500 mb-2">
          DEFAULT SHIPPING ADDRESS
        </p>

        <p class="font-medium mb-2">
          Add your delivery address
        </p>

        <p class="text-gray-500 mb-2">
          Save an address for a faster checkout next time.
        </p>

        <p class="font-semibold">
          + Add Address
        </p>

      </div>

      <!-- Bottom Buttons -->
      <div class="flex items-center gap-6">

        <button class="bg-black text-white px-6 py-4 rounded">
          Save Changes
        </button>

        <button class="text-gray-500">
          Cancel
        </button>

      </div>

    </div>

  </div>
</template>


