<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <ul>
      <create-contact
        @add-contact="addContact"
      /> 
      <friend-contact
        v-for="friend in friends"
        :name="friend.name"
        :email-adress="friend.email"
        :phone-number="friend.phone"
        :valid="friend.valid"
        :key="friend.id"
        :id="friend.id"
        @toggle-valid="toggleValid"
        @delete-contact="deleteContact"
      />
    </ul>
  </section>
</template>

<script>
import FriendContact from "./components/FriendContact.vue";
import CreateContact from "./components/CreateContact.vue";

export default {
  components: {
    FriendContact,
    CreateContact,
  },
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "Manuel Lorenz",
          phone: "0123 45678 90",
          email: "manuel@localhost.com",
          valid: true,
        },
        {
          id: "julie",
          name: "Julie Jones",
          phone: "0987 654421 21",
          email: "julie@localhost.com",
          valid: false,
        },
      ],
    };
  },
  methods: {
    toggleValid(id) {
      // тут сответственно этот метод обрабатывает @toggle-valid="toggleValid" event из дочернего компонента 
      // тут мы смотрим на payload из event в данном случае это id, находим нужного пользователся и меняем ему значения поля valid  
      // компонент обнавляется и закидывает обновленные пропсы обратно в дочерний элемент 
      
      const friend = this.friends.find(friend => friend.id === id)
      friend.valid = !friend.valid
    },

    addContact(nameForm, phoneForm, emailForm ){
      this.friends.push({name: nameForm, phone: phoneForm, email: emailForm})
    },

    deleteContact(id) {
      const friend = this.friends.find(friend => friend.id === id)
      console.log(friend)
      this.friends.splice(id , 1)
    }


  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: "Jost", sans-serif;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}
#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7em;
  display: inline-block;
}

#app form div {
  margin: 1rem 0;
}
</style>
