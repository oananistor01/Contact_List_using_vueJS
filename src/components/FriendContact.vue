<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>

    <button @click="toggleFavorite">Toggle Favorite</button>

    <button @click="toggleDetails">
      {{ detailsAreVisible ? 'Hide' : 'Show' }} Details
    </button>

    <button @click="$emit('delete', id)">Delete</button>

    <ul v-if="detailsAreVisible">
      <li class="contact-details">
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li class="contact-details">
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: ['name', 'phoneNumber', 'emailAddress', 'isFavorite'],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },

  emits: ['toggle-favorite', 'delete'],

  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    },
    //I used/called $emit directly on the Delete button above, without the 'this' keyword
    //see another option below
    // deleteFriend(){
    //   this.$emit('delete');
    // }
  },
};
</script>
