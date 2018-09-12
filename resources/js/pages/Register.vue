<template>
    <div class="container">
        <div class="card card-default">
            <div class="card-header">Inscription</div>

            <div class="card-body">
                <div class="alert alert-danger" v-if="has_error && !success">
                    <p v-if="error == 'registration_validation_error'">Erreur(s) de validation, veuillez consulter le(s) message(s) ci-dessous.</p>
                    <p v-else>Erreur, impossible de s'inscrire pour le moment. Si le problème persiste, veuillez contacter un administrateur.</p>
                </div>

                <form autocomplete="off" @submit.prevent="register" v-if="!success" method="post">

                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.email }">
                        <label for="email">E-mail</label>
                        <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email">
                        <span class="help-block" v-if="has_error && errors.email">{{ errors.email }}</span>
                    </div>

                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">
                        <label for="password">Mot de passe</label>
                        <input type="password" id="password" class="form-control" v-model="password">
                        <span class="help-block" v-if="has_error && errors.password">{{ errors.password }}</span>
                    </div>

                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">
                        <label for="password_confirmation">Confirmation mot de passe</label>
                        <input type="password" id="password_confirmation" class="form-control" v-model="password_confirmation">
                    </div>

                    <button type="submit" class="btn btn-default">Inscription</button>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        name: '',
        email: '',
        password: '',
        password_confirmation: '',
        has_error: false,
        error: '',
        errors: {},
        success: false
      }
    },

    methods: {
      register() {
        var app = this
        this.$auth.register({
          data: {
            email: app.email,
            password: app.password,
            password_confirmation: app.password_confirmation
          },
          success: function () {
            app.success = true
            this.$router.push({name: 'login', params: {successRegistrationRedirect: true}})
          },
          error: function (res) {
            console.log(res.response.data.errors)
            app.has_error = true
            app.error = res.response.data.error
            app.errors = res.response.data.errors || {}
          }
        })
      }
    }
  }
</script>
