<template>
  <nav class="navbar is-dark" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
        <span class="navbar-burger burger" data-target="navbarMenu">
          <span></span>
          <span></span>
          <span></span>
        </span>
      </div>
      <div id="navbarMenu" class="navbar-menu">
        <div class="navbar-start">
          <router-link :to="{ name: 'Home' }" class="navbar-item">
            Home
          </router-link>
        </div>
        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <router-link :to="{ name: 'Register' }" class="button is-primary"
                ><strong>Cadastrar</strong></router-link
              >
              <router-link :to="{ name: 'Login' }" class="button is-light">
                <strong> Entrar </strong>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import apiAuth from "../../api/auth";
export default {
  name: "Header",
  data() {
    return {
      authUser: [],
    };
  },
  mounted() {
    this.athenticated();
  },
  methods: {
    /* logout() {
      axios.post("/api/logout").then((r) => {
        window.location.href = "/spa/";
      });
    }, */
    athenticated() {
      apiAuth
        .athenticated()
        .then((r) => {
          this.authUser = r.data;
          console.log(this.authUser);
          localStorage.setItem("auth", "true");
        })
        .catch(() => {
          this.authUser = null;
          console.log(this.authUser);
          localStorage.removeItem("auth");
        });
    },
  },
};
</script>
