<template>
  <div class="player">
    <NuxtLink :to="'/'">Players</NuxtLink>
    <h1>#{{ number }}</h1>
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
export default {
  validate({ params }) {
    return !isNaN(+params.id)
  },
  asyncData({ params, env, error }) {
    const user = env.users.find(user => String(user.id) === params.id)
    if (!user) {
      return error({ message: 'User not found', statusCode: 404 })
    }
    return user
  },
  head() {
    return {
      title: this.name
    }
  }
}
</script>

<style scoped>
.player {
  font-family: sans-serif;
  width: 500px;
  margin: 1em;
}

ul {
  width: 500px;
  margin: 0 auto;
}

li {
  list-style-type: none;
}
</style>
