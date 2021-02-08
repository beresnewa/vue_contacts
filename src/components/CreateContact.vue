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
  data() {
    return {
      nameForm: '',
      phoneForm: '',
      emailForm: '',
    };
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
