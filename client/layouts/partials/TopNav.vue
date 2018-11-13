<template>
  <nav class="navbar is-light" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <nuxt-link :to="{ name: 'index' }" class="navbar-item">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
      </nuxt-link>

      <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start">
      </div>

      <div class="navbar-end">
        <no-ssr>
          <template v-if="!authenticated">
            <div class="navbar-item">
              <div class="buttons">
                <nuxt-link :to="{ name: 'auth-signin' }" class="button is-light">
                  Log in
                </nuxt-link>

                <nuxt-link :to="{ name: 'auth-signup' }" class="button is-info">
                  Sign up
                </nuxt-link>
              </div>
            </div>
          </template>

          <template v-if="authenticated">
            <div class="navbar-item has-dropdown is-hoverable">
              <a class="navbar-link">
                {{ user.name }}
              </a>

              <div class="navbar-dropdown is-right">
                <a class="navbar-item">
                  Log out
                </a>
              </div>
            </div>
          </template>
        </no-ssr>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  //
}
</script>
