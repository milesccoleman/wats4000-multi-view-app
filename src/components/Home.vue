<template>
  <div class="home">
    <div v-show="showForm" class="form-container">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>

      <p v-show="showError" class="error">Error. Please check the form and make sure all fields are filled in correctly.</p>

      <form v-on:submit.prevent="validateForm">

        <p><label for="username">
          <input type="text" id="username" v-model="username" placeholder="Please choose a username.">
        </Label></p>

        <p><label for="email">
          <input type="email" id="email" v-model="email" placeholder="Enter your email.">
        </Label></p>

        <p><label for="password">
          <input type="password" id="password" v-model="password" placeholder="Choose a password.">
        </Label></p>

        <p><label for="passwordVerify">
          <input type="password" id="passwordVerify" v-model="passwordVerify" placeholder="Verify your password.">
        </Label></p>

        <p><input type="submit" value="Submit"></p>
      </form>
    </div>
    <div v-show="!showForm" class="success-message">
      <h1>You're so close to being part of the super secret online website club!'</h1>
      <p>Please take our new-member survey. <router-link to="Survey">Click here</router-link></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      username: '',
      email: '',
      password: '',
      passwordVerify: '',
      showForm: true,
      showError: false
    }
  },
  methods: {
    validateForm: function () {
      if ((this.username != '') &&
        (this.email != '') &&
        (this.password === this.passwordVerify)) {
        this.showForm = false;
        }
      else {
        this.showError = true;
        }
      }
    }
  }
</script>

<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
