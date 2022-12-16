// src/App.vue
<template>
  <h1>IronContacts</h1>
  <button @click="addRandomContact()">Add Random Contact</button>
<table>
  <tr>
    <th>Picture</th>
    <th>Name</th>
    <th>Popularity</th>
    <th>Won Oscar</th>
    <th>Won Emmy</th>
  </tr>
  <tr v-for="contact in firstFiveContacts">
    <td><img :src="contact.pictureUrl" :alt="`${contact.name} picture`" width="100"></td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity }}</td>
    <td v-if="contacts.wonOscar">
      <i class="fas fa-trophy"></i>
    </td>
    <td v-if="contacts.wonEmmy">
      <i class="fas fa-trophy"></i>
    </td>
  </tr>
</table>
</template>

<script>
import CONTACTS from "./contacts.json"
  export default {
    data() {
      return {
        contacts: CONTACTS,
        firstFiveContacts: CONTACTS.slice(0, 5),
      }
    },
    computed: {
    
    },
    methods: {
      addRandomContact() {
        const randomContact = this.contacts[Math.floor(Math.random()*this.contacts.length)]
        console.log(randomContact)
        return this.firstFiveContacts.push(randomContact)
      }
    }
    // mounted() {
    //   this.addRandomContact
    // }
  } 
</script>

<style>
</style>

