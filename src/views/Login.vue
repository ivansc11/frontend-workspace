<template>
  <div>
    <div class="d-flex justify-content-center">
      <form v-on:submit.prevent="login">
        <div class="form-group">
          <label for="inputUsername">Nombre de usuario</label>
          <input
            class="form-control"
            id="inputUsername"
            placeholder="Ingresar usuario"
            v-model="username"
          />
        </div>
        <div class="form-group">
          <label for="inputPassword">Contraseña</label>
          <input
            type="password"
            id="inputPassword"
            class="form-control"
            placeholder="Contraseña"
            v-model="password"
          />
        </div>
        <button type="submit" class="btn btn-primary">Ingresar</button>
      </form>
    </div>
    <div class="d-block">
      <h1>{{error}}</h1>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: "",

      error: ""
    };
  },
  methods: {
    login() {
      const user = {
        username: this.username,
        password: this.password
      };
      axios.post("http://localhost:3000/api/login", user).then(
        res => {
          if (res.status === 200) {
            localStorage.setItem('token', res.data.token)
            this.error = "";
            this.$router.push("/");
          }
        },
        err => {
          this.error = err.response.data.error;
        }
      );
    }
  }
};
</script>

<style>
</style>