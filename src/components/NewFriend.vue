<template>
  <!-- when Add Contact button is pressed, the form is automatically sumbitted. 
  Therefore we add a submit event to prevent the page refresh -->
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="enteredName" />
    </div>
    <div>
      <label>Phone</label>
      <input type="tel" v-model="enteredPhone" />
    </div>
    <div>
      <label>E-Mail</label>
      <input type="email" v-model="enteredEmail" />
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-contact'],
  data() {
    return {
      //we store here the users input data. we bind them in the template above with v-model(short for v-bind and v-on)
      enteredName: '',
      enteredPhone: '',
      enteredEmail: '',
    };
  },
  methods: {
    submitData() {
      this.$emit(
        'add-contact',
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      );
    },
  },
};
</script>
