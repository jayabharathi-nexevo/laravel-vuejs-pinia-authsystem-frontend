<script setup>
import { useAuthStore } from '../stores/auth';

const authStore = useAuthStore();
</script>


<template>
    <header class="text-gray-600 body-font">
  <div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
    <a class="flex title-font font-medium items-center text-gray-900 mb-4 md:mb-0">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-10 h-10 text-white p-2 bg-indigo-500 rounded-full" viewBox="0 0 24 24">
        <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"></path>
      </svg>
      <span class="ml-3 text-xl">Tailblocks</span>
    </a>
    <nav class="md:ml-auto flex flex-wrap items-center text-base justify-center">
      <router-link :to="{name:'Home'}" class="mr-16 hover:text-gray-900 cursor-pointer bg-blue-300 px-4 py-2 ">Home</router-link>
    
    <template v-if="!authStore.user">
        <router-link :to="{name:'Login'}" class="mr-16 hover:text-gray-900 cursor-pointer bg-blue-300 px-4 py-2">Login</router-link>
        <router-link :to="{name:'Register'}" class="mr-16 hover:text-gray-900 cursor-pointer bg-blue-300 px-4 py-2">Register</router-link>    
    </template>
    <template v-else>
        <button @click="authStore.handleLogout" class="mr-16 hover:text-gray-900 cursor-pointer bg-blue-300 px-4 py-2">
             Logout
        </button>
    </template>
     
    </nav>
   
  </div>
</header>
</template>