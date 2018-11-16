<template>
  <section class="hero">
    <div class="hero-body">
      <div class="container">
        <div class="column is-4 is-offset-4">
          <h1 class="title has-text-grey has-text-centered">Join us</h1>

          <div class="box">
            <form method="" @submit.prevent="submit">
              <div class="field">
                <label for="email" class="label">Email address</label>
                <div class="control">
                  <input class="input is-medium" :class="{ 'is-danger': errors.email }" type="email" id="email" v-model="form.email">

                  <p class="help is-danger" v-if="errors.email">{{ errors.email[0] }}</p>
                </div>
              </div>

              <div class="field">
                <label for="name" class="label">Full name</label>
                <div class="control">
                  <input class="input is-medium" :class="{ 'is-danger': errors.name }" id="name" v-model="form.name">

                  <p class="help is-danger" v-if="errors.name">{{ errors.name[0] }}</p>
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
                <button class="button is-block is-info is-medium is-fullwidth">Sign up</button>
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
        name: '',
        password: ''
      }
    }
  },
  methods: {
    async submit () {
      await this.$axios.post('register', this.form)

      await this.$auth.login({
        data: {
          email: this.form.email,
          password: this.form.password
        }
      })

      this.$router.push({
        name: 'index'
      })
    }
  }
}
</script>
