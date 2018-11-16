<template>
  <section class="hero">
    <div class="hero-body">
      <div class="container">
        <div class="column is-4 is-offset-4">
          <h1 class="title has-text-grey has-text-centered">Sign in</h1>

          <div class="box">
            <form action="#" @submit.prevent="submit">
              <div class="field">
                <label for="email" class="label">Email address</label>
                <div class="control">
                  <input class="input is-medium" :class="{ 'is-danger': errors.email }" type="email" id="email" v-model="form.email">

                  <p class="help is-danger" v-if="errors.email">{{ errors.email[0] }}</p>
                </div>
              </div>

              <div class="field">
                <label for="password" class="label">Password</label>
                <div class="control">
                  <input class="input is-medium" :class="{ 'is-danger': errors.password }" type="password" id="password" v-model="form.password">

                  <p class="help is-danger" v-if="errors.password">{{ errors.password[0] }}</p>
                </div>
              </div>

              <div class="field">
                <button class="button is-block is-info is-medium is-fullwidth">Log in</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  middleware: 'guest',
  data () {
    return {
      form: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async submit () {
      await this.$auth.loginWith('local', {
        data: this.form
      }),

      this.$router.push({
        path: this.$route.query.redirect || '/'
      })
    }
  }
}
</script>
