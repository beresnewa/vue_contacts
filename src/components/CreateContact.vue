<template>
  <form>
    <div>
      <label>Name</label>
      <input type="text" v-model="nameForm"/>
    </div>
    <div>
      <label>Phone</label>
      <input type="text" v-model="phoneForm"/>
    </div>
    <div>
      <label>Email</label>
      <input type="text" v-model="emailForm"/>
    </div>
    <input type="submit" @click="addContact">
     
  </form>
</template>

<script>
export default {
  name: "new-contact", // необезательное свойство 
  props: {
    id: String,
    name: {
      type: String,
      required: true,
      default: "0", 
      validator: function(value) {
        return value.length > 0;
      },
    },
    phoneNumber: String,
    emailAdress: String,
  },

  data() {
    return {
      nameForm: '',
      phoneForm: '',
      emailForm: '',
    };
  },

  mounted() {
    this.nameFrom = this.name;
    this.phoneForm = this.phoneNumber;
    this.emailForm = this.emailAdress;
  },

  methods: {
    addContact(event){
      event.preventDefault();

      this.$emit("add-contact", this.nameForm, this.phoneForm, this.emailForm)
    }
  },
};
</script>

<style></style>
