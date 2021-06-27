<template>
  <div class="card">
    <div class="card-header">
      <div class="card-header-title">Cadastre-se</div>
    </div>
    <div class="card-content">
      <div class="column is-8 is-offset-2">
        <form class="box">
          <div class="field">
            <label class="label">Nome</label>
            <div class="control">
              <input class="input" v-model="form.name" type="text" />
            </div>
          </div>
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
          <div class="field">
            <label class="label">Cornfirme a senha</label>
            <div class="control">
              <input
                class="input"
                v-model="form.password_confirmation"
                type="password"
              />
            </div>
          </div>
          <div class="field is-grouped">
            <div class="control">
              <button @click.prevent="saveForme" class="button is-link">Cadastrar</button>
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
  name: "Register",
  data() {
    return {
      form: {
        name: "",
        email: "",
        password: "",
        password_confirmation: "",
      },
      errors: [],
    };
  },
  methods: {
    saveForme() {
      apiAuth
        .register(this.form)
        .then((r) => {
          console.log(r);
          /* this.$toastr.s("Cadastrado com sucesso!"); */
          /* window.location.href = "/spa/"; */
        })
        .catch((error) => {
          console.log(error.response.data);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
