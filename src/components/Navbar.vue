<template>
  <nav class="bg-white shadow-md fixed w-full z-50">
    <div class="container mx-auto px-6 py-4 flex justify-between items-center">
      <!-- Logo / Name -->
      <!-- <router-link to="/" class="text-2xl font-bold text-blue-600"> DC Breckle </router-link> -->

      <!-- Desktop Links -->
      <ul class="hidden md:flex space-x-6 text-gray-700 font-semibold">
        <li>
          <router-link to="/" class="hover:text-blue-600 transition">Home</router-link>
        </li>
        <li>
          <!-- <router-link to="#projects" class="hover:text-blue-600 transition">Projects</router-link> -->
        </li>
        <li>
          <!-- <router-link to="#about" class="hover:text-blue-600 transition">About</router-link> -->
        </li>
        <li>
          <!-- <router-link to="#contact" class="hover:text-blue-600 transition">Contact</router-link> -->
        </li>
      </ul>

      <!-- Mobile Hamburger -->
      <button @click="toggleMenu" class="md:hidden text-gray-700 focus:outline-none">
        <svg
          v-if="!menuOpen"
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div v-if="menuOpen" class="md:hidden bg-white shadow-md">
      <ul class="flex flex-col space-y-2 px-6 py-4 text-gray-700 font-semibold">
        <li>
          <router-link @click="closeMenu" to="/">Home</router-link>
        </li>
        <!-- <li>
          <router-link @click="closeMenu" to="#projects">Projects</router-link>
        </li>
        <li>
          <router-link @click="closeMenu" to="#about">About</router-link>
        </li>
        <li>
          <router-link @click="closeMenu" to="#contact">Contact</router-link>
        </li> -->
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}
</script>
