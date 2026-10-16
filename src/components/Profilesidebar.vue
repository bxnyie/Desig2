<script setup lang="ts">
import { ref } from 'vue'


export type AccountSection =
    | 'User detailes'
    | 'Past orders'
    | 'Login and security'
    | 'Payment methods'
    | 'Address book'
    | 'Notifications'
    | 'Privacy settings'
    | 'Delete account'
    | 'Logout'

const props = defineProps<{
    activesection : AccountSection
}>()

const emit = defineEmits<{
    selectsection: [section: AccountSection] | ['logout']
}>()


const navigationItems : { id: AccountSection, label: string }[] = [
    { id: 'User detailes', label: 'User detailes' },
    { id: 'Past orders', label: 'Past orders' },
    { id: 'Login and security', label: 'Login and security' },
    { id: 'Payment methods', label: 'Payment methods' },
    { id: 'Address book', label: 'Address book' },
    { id: 'Notifications', label: 'Notifications' },
    { id: 'Privacy settings', label: 'Privacy settings' },
    { id: 'Delete account', label: 'Delete account' },
    { id: 'Logout', label: 'Logout' }
  
]
</script>

<template>
  <nav aria-label="Profile navigation">
    <button
      v-for="item in navigationItems"
      :key="item.id"
      type="button"
      class="w-full cursor-pointer p-4 text-left hover:bg-gray-100"
      :class="{ 'bg-gray-100': props.activesection === item.id }"
      :aria-current="props.activesection === item.id ? 'page' : undefined"
      @click="emit('selectsection', item.id)"
    >
      {{ item.label }}
    </button>
  </nav>
</template>
