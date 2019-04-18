<template>
  <div class="player">
    <h1>Players</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        <NuxtLink :to="'/users/' + user.id">{{ user.name }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  asyncData({ env }) {
    return { users: env.users }
  }
}
</script>

<style scoped>
.player {
  font-family: sans-serif;
  width: 500px;
}

h1 {
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
