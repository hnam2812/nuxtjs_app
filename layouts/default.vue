
<template>
  <div id="app">
    <v-app>
      <v-toolbar app light>
        <v-toolbar-title><a href="/">Auth example</a></v-toolbar-title>
        <v-spacer />
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat href="/user/login" v-if="!this.$auth.$state.loggedIn">Login</v-btn>
          <v-btn flat @click="logout" v-else>Logout</v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <v-content>
        <v-container fluid>
          <nuxt/>
        </v-container>
      </v-content>
    </v-app>
  </div>
</template>

<script>
export default {
  methods: {
    logout: function () {
      this.$auth.logout().then(() => {
        location.replace('/user/login')
      })
    }
  }
}
</script>