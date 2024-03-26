<template>
  <div class='px-8'> 
    <p class="montserrat text-3xl font-medium mb-10">Your Contacts</p>
    <div class='grid grid-cols-3 gap-5 items-center justify-center'>
      <div v-for="contact in contacts" :key="contact.objectId" class="contact montserrat bg-[#FFFFFF] hover:shadow-lg mb-4 rounded-lg flex flex-col gap-3 p-3 w-11/12 items-center">
        <p class="text-lg">Name: {{ contact.name }}</p>
        <p class="text-lg">Email: {{ contact.email }}</p>
        <p class="text-lg">Phone: {{ contact.phone }}</p>
        <p class="text-lg">Address: {{ contact.address }}</p>
        <p class="text-lg">Company: {{ contact.company }}</p>
        <div class="mt-5">
          <button @click="deleteContact(contact.objectId)" class="px-4 py-2 hover:bg-[#333333] hover:text-white rounded-lg font-medium">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Parse from 'parse';

const contacts = ref([]);

const fetchContacts = async () => {
  try {
    // Note that 'getContacts' would refer to your Cloud function
    contacts.value = await Parse.Cloud.run('getContacts');
  } catch (error) {
    console.error('Failed to fetch contacts', error);
  }
};

const deleteContact = async (objectId) => {
  try {
    await Parse.Cloud.run('deleteContact', { objectId });
    contacts.value = contacts.value.filter((contact) => contact.objectId !== objectId);
  } catch (error) {
    console.error('Failed to delete contact', error);
  }
};

onMounted(fetchContacts);
</script>