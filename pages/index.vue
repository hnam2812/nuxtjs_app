<template>
  <v-layout>
    <v-flex>
      <v-list>
        <v-list-tile v-for="user in users" :key="user.id">
          <v-list-tile-content>{{user.email}}</v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  middleware: 'auth',
  data () {
    return {
      users: []
    }
  },
  methods: {
    async listUsers() {
      this.users = await this.$axios.$get('/users')
    }
  },
  mounted () {
    this.listUsers()
  }
}
</script>