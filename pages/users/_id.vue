<template>
  <section>
    <h1>
      {{ user.name }}
    </h1>
    <hr>
    <p><strong>Email:</strong> {{ user.email }}</p>
    <p><strong>Phone:</strong> {{ user.phone }}</p>
  </section>
</template>

<script>
export default {
  async asyncData ({ $axios, params }) {
    const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id)
    return { user }
  },
  validate ({ params }) {
    return /^\d+$/.test(params.id)
  }
}
</script>
