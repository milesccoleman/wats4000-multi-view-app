<template>
  <div class="secret">
  <div v-show="showForm" class="form-container">
      <h1>You've reached the secret!</h1>
      <p>Want to see it?</p>
      <form v-on:submit.prevent="validateForm">

      <p v-show="showError" class="error">Error. Please check the form and make sure all fields are filled in correctly.</p>

        <p>
          <label v-for="secret in secretOptions">
            <input type="checkbox" v-model="cb" v-bind:value="secret.value">
            {{ secret.text }}
          </label>
        </p>

        <p><input type="submit" value="Submit"></p>
      </form>

     <p><router-link to="Home">Home</router-link></p>
     <p><router-link to="Survey">Take Survey Again</router-link></p>
  </div>
        <div v-show="!showForm" class="success-message">
        <h1>Awesome! <br>Here it is!</h1>
        <p><img src="https://media.giphy.com/media/26AHG5KGFxSkUWw1i/giphy.gif"></p>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Secret',
  data () {
    return {
      cb: [],
      showForm: true,
      showError: false,
      secretOptions: [
        {
            text: 'Yes!',
            value: 1
        },
        {
            text: 'No!',
            value: 0
        },
      ]
    }
  },
  methods: {
    validateForm: function () {
      if ((this.cb > 0)) {
        this.showForm = false;
        }
      else {
        this.showError = true;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
a {
  color: #42b983;
}
</style>

