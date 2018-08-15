<template>
  <v-app id="sign-up-form">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Login</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form @submit.prevent="login()">
                  <v-text-field autocomplete="new-password" prepend-icon="person"
                    label="Email" type="text" v-model="user.email"></v-text-field>
                  <v-text-field autocomplete="new-password" prepend-icon="lock"
                    label="Password" type="password" v-model="user.password"></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click.prevent="login()">Login</v-btn>
              </v-card-actions>
               <v-card-actions>
                <v-spacer></v-spacer>
                <a href="/user/sign_up">New user?</a>
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
  middleware: false,
  data () {
    return {
      user: {email: '', password: ''},
      error: null
    }
  },
  methods: {
    login: function() {
      this.$auth.login({
        data: {
          user: {
            email: this.user.email,
            password: this.user.password
          }
        }
      }).then((res) => location.replace('/'))
      .catch(e => {this.error = e + ''})
    }
  },
  mounted () {
  }
}
</script>
