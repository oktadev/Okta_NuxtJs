<template>
  <div id="page-content" class="p-4">
    <a class="btn btn-primary" @click="$auth.loginWith('okta')">Login with Okta </a>
  </div>
</template>


<script>
export default {
  middleware: ['auth'],
  data() {
    return {}
  },
  beforeMount() {
    if (this.$auth.$state.loggedIn) window.location = '/Dashboard'
  }
}
</script>