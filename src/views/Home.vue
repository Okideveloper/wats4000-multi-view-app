<template>
  <div class="home">
    <div class="form-container" v-show="showForm">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>

      <p
        class="error"
        v-show="showError"
      >Please check the information you have entered. Be sure to fill in all the fields.</p>
      <form v-on:submit.prevent="validateForm">
        <!-- Username -->
        <p>
          <label for="username">
            Username
            <input type="username" id="username" v-model="username">
          </label>
        </p>

        <!-- email -->
        <p>
          <label for="email">
            E-mail
            <input type="email" id="email" v-model="email">
          </label>
        </p>

        <!-- Password -->
        <p>
          <label for="password">
            Password
            <input type="password" id="password" v-model="password">
          </label>
        </p>
        <!-- Password Verify-->
        <p>
          <label for="passwordVerify">
            Verify Password
            <input
              type="password"
              id="passwordVerify"
              v-model="passwordVerify"
            >
          </label>
        </p>

        <p>
          <input type="submit" value="Submit">
        </p>
      </form>
    </div>
    <div class="success-message" v-show="!showForm">
      <h1>Thank you for signing up!</h1>
      <p>
        Please a second and take our new membership survey.
        <router-link to="/survey">Click here</router-link>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      username: "",
      email: "",
      password: "",
      passwordVerify: "",
      showForm: true,
      showError: false
    };
  },
  methods: {
    validateForm: function() {
      if (
        this.username !== "" &&
        this.email !== "" &&
        this.password === this.passwordVerify
      ) {
        this.showForm = false;
      } else {
        this.showError = true;
      }

      // Validate the form by checking the following values:
      // username must not be blank
      // email must not be blank
      // password and passwordVerify must be equal
      //
      // When the form is validated, show the .success-message content
      // If the form is invalid, show the form error message
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1,
h2 {
  font-family: Verdana;
  font-weight: 600;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0;
}

a {
  color: #424ab9;
}
</style>
