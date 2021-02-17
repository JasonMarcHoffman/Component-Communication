<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="deleteContact">Delete Contact</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
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
    // prop validations
    id: {type: String, required: true},
    name: {type: String, required: true},
    phoneNumber: {type: String, required: true},
    emailAddress: {type: String, required: true},
    isFavorite: {
      type: Boolean, 
      required: false, 
      default: false,
      // validator: function(value) {
      //   return value === '1' || value === '0'
      // }
    },
  },
  // document the component by showing the emits
  emits: ['toggle-favorite', 'delete-contact'],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite: function() {
      this.$emit('toggle-favorite', this.id)
    },
    deleteContact: function() {
      this.$emit('delete-contact', this.id)
    }
  },
};
</script>