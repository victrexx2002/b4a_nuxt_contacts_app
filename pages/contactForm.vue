<template>
  <div>
    <p class="montserrat text-2xl font-medium text-center">Fill the form below to create a contact</p>
    <form @submit.prevent="createContact" class="flex flex-col gap-8 items-center mt-10">
      <input v-model="contact.name" type="text" placeholder="Name" required class="w-1/2 p-3 hover:shadow-lg outline-none montserrat"/>
      <input v-model="contact.email" type="email" placeholder="Email" required class="w-1/2 p-3 hover:shadow-lg outline-none montserrat"/>
      <input v-model="contact.phone" type="tel" placeholder="Phone" required class="w-1/2 p-3 hover:shadow-lg outline-none montserrat"/>
      <input v-model="contact.address" type="text" placeholder="Address" required class="w-1/2 p-3 hover:shadow-lg outline-none montserrat"/>
      <input v-model="contact.company" type="text" placeholder="Company" class="w-1/2 p-3 hover:shadow-lg outline-none montserrat"/>
      <div>
        <button class="px-4 py-2 hover:bg-[#333333] hover:text-white rounded-lg font-medium" type="submit">
          Submit
        </button>
      </div>
      <p v-if="message" :class="{ error: isError }">{{ message }}</p>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Parse from 'parse';


const contact = ref({
  name: '',
  email: '',
  phone: '',
  address: '',
  company: '',
});
const message = ref('');
const isError = ref(false);

const createContact = async () => {
  try {
    await Parse.Cloud.run('createContact', { ...contact.value });
    message.value = 'Contact created successfully!';
    isError.value = false;
    
    contact.value = { name: '', email: '', phone: '', address: '', company: '' };
  } catch (error) {
    message.value = `Error: ${error.message}`;
    isError.value = true;
  }
};
</script>

<style>
.error {
  color: red;
}
</style>