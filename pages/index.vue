<template>
    <div class="welcome montserrat flex flex-col gap-8 items-center mt-10">
      <h1 class="text-4xl">Welcome to {{ appName }}!</h1>
      <p class="text-[#888888] font-md text-md w-1/2">This application helps you manage your contacts. You can view existing contacts, add new ones, and keep your contact information organized.</p>
      <NuxtLink to="/contactForm">
        <button class="px-4 py-2 hover:bg-[#333333] hover:text-white rounded-lg font-medium">
          Add Contact
        </button>
      </NuxtLink>
    </div>
  </template>
  
  <script setup>
  const appName = 'Contact Book'; // Replace with your actual app name
  </script>
  
  <style scoped>
  .welcome {
    text-align: center;
    padding: 2rem;
  }
  </style>