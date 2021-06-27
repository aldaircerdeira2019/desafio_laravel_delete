<template>
  <div class="card">
    <div class="card-header">
      <div class="card-header-title">Entrar</div>
    </div>
    <div class="card-content">
      <div class="column is-8 is-offset-2">
        <form class="box">
          <div class="field">
            <label class="label">Email</label>
            <div class="control">
              <input class="input" v-model="form.email" type="text" />
            </div>
          </div>
          <div class="field">
            <label class="label">Senha</label>
            <div class="control">
              <input class="input" v-model="form.password" type="password" />
            </div>
          </div>
          <div class="field is-grouped">
            <div class="control">
              <button @click.prevent="loginUser" class="button is-link">
                Entrar
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
import apiAuth from "../../api/auth";
export default {
  name: "Login",
  data() {
    return {
      form: {
        email: "",
        password: "",
      },
      errors: [],
    };
  },
  methods: {
    loginUser() {
      apiAuth
        .login(this.form)
        .then((r) => {
          console.log(r);
          /* this.$router.push({ name: "home"});  */
          //window.location.href = "/#/";
        })
        .catch((error) => {
          console.log(error.response.data);
          this.errors = error.response.data.errors;
          this.form.password = null;
        });
    },
  },
};
</script>
