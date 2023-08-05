<script setup>
import { onMounted } from 'vue';
import { useAuthStore } from '../stores/auth';

const authStore = useAuthStore();


onMounted(async() => {

    await authStore.getUser();
  
});

</script> 

<template>
<div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
    <div class="container" v-if="authStore.user">
        <h1>{{ authStore.user.name }}</h1>
        <p>{{ authStore.user.email }}</p>        
    </div>
    <div v-else>
        Go and Login
    </div>
 
    </div>
</template>