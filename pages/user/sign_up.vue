<template>
  <v-app id="sign-up-form">
    <v-content>
      <v-container fluid fill-height>
        <v-layout justify-center>
          <v-flex md8>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Sign up</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form @submit.prevent="onSignUpSubmit()">
                  <v-text-field autocomplete="new-password"
                    label="Email" type="text" v-model="user.email"></v-text-field>
                  <v-text-field autocomplete="new-password"
                    label="Password" type="password" v-model="user.password"></v-text-field>
                  <v-text-field autocomplete="new-password"
                    label="First Name" type="text" v-model="user.first_name"></v-text-field>
                  <v-text-field autocomplete="new-password"
                    label="Last Name" type="text" v-model="user.last_name"></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click.prevent="onSignUpSubmit()">Sign up</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      user: {email: '', password: '', last_name: '', first_name: ''}
    }
  },
  methods: {
    async onSignUpSubmit() {
      await this.$axios.$post('/users', {user: this.user})
    }
  },
  mounted () {
  }
}
</script>