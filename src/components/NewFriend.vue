<template>
  <form @submit.prevent="addFriend">
    <div>
      <label>Name:</label>
      <input type="text" v-model="name">
    </div>
    <div>
      <label>Phone Number:</label>
      <input type="text" v-model="phone">
    </div>
    <div>
      <label>Email:</label>
      <input type="email" v-model="email">
    </div>
    <button>Add Friend</button>
  </form>
</template>

<script>
export default {
  data: function() {
    return {
      name: '',
      phone: '',
      email: ''
    }
  },
  methods: {
    addFriend: function() {
      this.$emit('add-friend', this.name, this.phone, this.email)
    }
  }
}
</script>

<style scoped>
form {
  border: 1px solid lightgrey;
  padding: 1rem;
  width: 600px;
  margin: 0 auto;
  border-radius: 5px;
}
div {  
  display: flex;
  flex-direction: column;
}
label {
  font-size: 12px;
  padding: 6px 0;
}
button {
  margin-top: 1rem;
}
</style>