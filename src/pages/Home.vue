<template>
  <b-col>
    <h2>Welcome to the Cloud Festivals Website</h2>
    <label for="email">Email: </label>
    <input type="email" v-model="form.email" />
    <br />
    <label for="password">Password: </label>
    <input type="password" v-model="form.password" />
    <br />
    <button @click="login()">Submit</button>
  </b-col>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      form: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    login() {
      axios
        .post(`https://festivals-api.herokuapp.com/api/users/login`, {
          email: this.form.email,
          password: this.form.password,
        })
        .then((response) => {
          console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
          console.log(error.response);
        });
    },
  },
};
</script>
