<template>
  <div class="wrapper">
    <nav class="sidebar">
      <b-nav
        vertical
        class="w-25">
        <b-nav-item active>Active</b-nav-item>
        <b-nav-item>Link</b-nav-item>
        <b-nav-item>Another Link</b-nav-item>
        <b-nav-item disabled>Disabled</b-nav-item>
      </b-nav>
    </nav>
    <div class="main">
      <nav>
        test
      </nav>
      <main class="container">
        <nuxt />
      </main>
    </div>
    <b-alert show>Default Alert</b-alert>

    <b-alert
      variant="success"
      show>Success Alert</b-alert>

    <b-alert
      :show="showDismissibleAlert"
      variant="danger"
      dismissible
      @dismissed="showDismissibleAlert=false">
      Dismissible Alert!
    </b-alert>

    <b-alert
      :show="dismissCountDown"
      dismissible
      variant="warning"
      @dismissed="dismissCountDown=0"
      @dismiss-count-down="countDownChanged">
      <p>This alert will dismiss after {{ dismissCountDown }} seconds...</p>
      <b-progress
        :max="dismissSecs"
        :value="dismissCountDown"
        variant="warning"
        height="4px" />
    </b-alert>

    <b-btn
      variant="info"
      class="m-1"
      @click="showAlert">
      Show alert with count-down timer
    </b-btn>
    <b-btn
      variant="info"
      class="m-1"
      @click="showDismissibleAlert=true">
      Show dismissible alert ({{ showDismissibleAlert?'visible':'hidden' }})
    </b-btn>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dismissSecs: 10,
      dismissCountDown: 0,
      showDismissibleAlert: false
    }
  },
  methods: {
    countDownChanged(dismissCountDown) {
      this.dismissCountDown = dismissCountDown
    },
    showAlert() {
      this.dismissCountDown = this.dismissSecs
    }
  }
}
</script>

<style>
</style>
