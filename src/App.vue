<script setup lang="ts">
import { ref } from 'vue'
import Footer from './components/Footer.vue'
import Header from './components/Header.vue'
import Home from './views/Home.vue'
import Product from './views/Product.vue'
import Elements from './views/Elements.vue'
import Profile from './views/Profile.vue'

const currentView = ref('home')



</script>

<template>
  <Header :currentView="currentView" @navigate="currentView = $event" />

  <main class="flex-grow">
    <Home v-if="currentView === 'home'" />
    <Product v-else-if="currentView === 'products'" />
    <Elements v-else-if="currentView === 'elements'" />
    <Profile v-else-if="currentView === 'profile'" />
  </main>

  <Footer />
</template>