<template>
  <div>
    <NuxtLayout>
      <header class="flex justify-between p-8 roboto font-light">
        <NuxtLink to="/">
          <p class="text-2xl">Contact Book</p>
        </NuxtLink>

        <nav class="flex gap-5 text-md">
          <NuxtLink to="/contactsList" class="hover:text-[#888888]">Contacts</NuxtLink>
          <NuxtLink to="/contactForm" class="hover:text-[#888888]">Add Contact</NuxtLink>
        </nav>
      </header>
      <main>
        <NuxtPage />
      </main>
    </NuxtLayout>
  </div>
</template>

<script setup>
import Parse from 'parse';

// Initialize Parse SDK
Parse.initialize("YiMmHyRydLqZfYcSWUcr7iLsWeqP6Mi9rfSD1JPG", "uGA2ciKLF5MsTCRSZNf8k8RZgsBdOQ0ee1E3ldXx");
Parse.serverURL = "https://parseapi.back4app.com";
</script>