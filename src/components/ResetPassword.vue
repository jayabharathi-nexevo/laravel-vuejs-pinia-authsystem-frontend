<script setup>
import { useAuthStore } from '../stores/auth';
import { ref } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();

const authStore = useAuthStore();

const form = ref({
   
    password:'',
    password_confirmation:'',
    token:route.params.token,
    email:route.query.email,

});

</script>

<template>

<div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
  <div class="sm:mx-auto sm:w-full sm:max-w-sm">
   
    <h2 class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">Reset Password</h2>
  </div>

  <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
    <form class="space-y-6" action="#" method="POST" @submit.prevent="authStore.handleResetPassword(form)">
        <div class="flex w-full bg-green-400" v-if="authStore.status">
        <span class="p-3 text-white ">{{ authStore.status  }}</span>
      </div>
     <div>
        <div class="flex items-center justify-between">
          <label for="password" class="block text-sm font-medium leading-6 text-gray-900">New Password</label>         
        </div>
        <div class="mt-2">
          <input id="password" name="password" v-model="form.password" type="password" autocomplete="current-password"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
          <div v-if="authStore.errors.password" class="flex">
            <span class="text-red-400">{{ authStore.errors.password[0] }}</span>        
        </div>
        </div>
      </div>

      <div>
        <div class="flex items-center justify-between">
          <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Confirm Password</label>         
        </div>
        <div class="mt-2">
          <input id="password" name="password" v-model="form.password_confirmation" type="password" autocomplete="current-password"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
        </div>
      </div>

      <div>
        <button type="submit" class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Sign in</button>
      </div>
    </form>

   
  </div>
</div>

</template>