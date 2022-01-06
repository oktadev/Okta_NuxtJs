<template>
  <div>
    <b-container>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">Posts</b-navbar-brand>
        <b-navbar-nav>
          <b-nav-item href="/dashboard"> Dashboard </b-nav-item>
        </b-navbar-nav>

        <b-navbar-nav v-if="loggedIn" class="ml-auto">
          <b-button @click="logout" size="sm" class="my-2 my-sm-0" type="submit"
            >Logout
          </b-button>
        </b-navbar-nav>

        <b-navbar-nav v-else class="ml-auto">
          <b-button @click="login" size="sm" class="my-2 my-sm-0" type="submit"
            >Login
          </b-button>
        </b-navbar-nav>

      </b-navbar>

      <nuxt />

      <footer id="sticky-footer" class="py-4 bg-dark text-white-50">
        <div class="fluid-container footer">
          <small>Copyright &copy;{{ year }} </small>
          <br />

          A small app built with
          <a href="https://nuxtjs.org/" target="blank">Nuxt</a>, Protected by
          <a href="https://www.okta.com/" target="blank">Okta</a>, Written by
          <a href="https://profile.fishbowlllc.com" target="blank">Nik Fisher</a
          >.
        </div>
      </footer>
    </b-container>
  </div>
</template>

<style scoped>
.fluid-container.footer > *:last-child {
  margin-bottom: 0px;
  color: #fff;
}
</style>


<script>
export default {
  data() {
    return {
      loggedIn: this.$auth.$state.loggedIn,
      year: new Date().getFullYear(),
    }
  },
  methods: {
    logout() {
      this.$auth.logout();
    },
    login() {
      this.$auth.loginWith('okta').then(result => window.location = "/Dashboard");
    }
  },
}
</script>