<template>
  <div >
    <h1>Contact List</h1>
    <form @submit.prevent>
        <label>Name</label>
        <input v-model="newContact.name" type="text" placeholder="Name"> <br>
        <label>Email</label>
        <input v-model="newContact.email" type="text" placeholder="Email"> <br>
        <button @click="addContact" type="submit">Add Contact</button>
    </form>
    <table align="center">
        <thead>
            <th>Name</th>
            <th>Email</th>
        </thead>
        <tbody>
            <tr v-for="contact in contacts" :key="contact.id">
               <td>{{contact.name}}</td> 
               <td>{{contact.email}}</td> 
               <button @click="deleteContact(contact)">Delete</button>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ContactList',
  data() {
      return {
          contacts: [
              {id: 1, name:"John", email:"example1@gmail.com"},
              {id: 2, name:"Jack", email:"example2@gmail.com"},
              {id: 3, name:"Susan", email:"example3@gmail.com"},
              {id: 4, name:"Jane", email:"example4@gmail.com"}
          ],
          newContact: {

          }
      };
  },
  methods: {
      addContact() {
          this.contacts.push(this.newContact);
          this.newContact = {}
      },
      deleteContact(contact) {
          let indexOfContactToDelete = this.contacts.indexOf(contact);
          this.contacts.splice(indexOfContactToDelete, 1);
      }
  }
}
</script>