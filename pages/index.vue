<template>
  <section class="container">
    <img src="~assets/images/logo.png" alt="Nuxt.js Logo" class="logo"/>
    <h1 class="title">
      USERS
    </h1>
    <ul class="users">
      <li v-for="(user, index) in users" :key="index" class="user">
        <nuxt-link :to="{ name: 'id', params: { id: user.username }}">
          {{ user.username }}
        </nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
  import axios from '~/plugins/axios'

  export default {
    async asyncData () {
      let {data} = await axios.get('/api/users', {params: {name: 'test'}})
      return {users: data.data}
    },
    head () {
      return {
        title: 'Users'
      }
    }
  }
</script>

<style scoped>
  .title {
    margin: 30px 0;
  }

  .users {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .user {
    margin: 10px 0;
  }
</style>
