<template>
  <section>
    <h1>
      List of Users
    </h1>
    <ul class="list-group">
      <li v-for="user of users" :key="user.id" class="list-group-item">
        <a href="#" @click.prevent="openUser(user)">{{ user.name }}</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  async fetch ({ store }) {
    if (store.getters.users.length === 0) {
      await store.dispatch('fetch')
    }
  },
  computed: {
    users () {
      return this.$store.getters.users
    }
  },
  methods: {
    openUser (user) {
      this.$router.push('/users/' + user.id)
    }
  }
}
</script>
