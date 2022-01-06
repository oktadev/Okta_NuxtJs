<template>
  <div id="page-content">
    <b-jumbotron
      style="margin-top: 5vh"
      header="Lets Get Some Posts"
      lead="A Simple App with Nuxt and Okta"
    >
      <p>For more information visit their websites</p>
      <b-button variant="primary" href="https://nuxtjs.org/" target="blank"
        >Nuxt</b-button
      >
      <b-button
        variant="outline-primary"
        href="https://www.okta.com/"
        target="blank"
        >Okta</b-button
      >
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  beforeMount() {
    if (this.$auth.$state.loggedIn) window.location = '/Dashboard'
  },
}
</script>