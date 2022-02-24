<template>
  <div>
    <form @submit.prevent="getUser">
      <input type="text" placeholder="username" v-model="user.login" />
      <button v-on:click="addUser">Buscar</button>
    </form>
    <div>
      {{ user }}
    </div>
  </div>
</template>

<script>
import User from "../services/users";

export default {
  data() {
    return {
      user: {
        login: "",
        id: "",
        avatar_url: "",
        html_url: "",
        repos_url: "",
        received_events_url: "",
        type: "",
        name: "",
        blog: "",
        location: "",
        email: "",
        bio: "",
        twitter_username: "",
        public_repos: "",
        public_gists: "",
        followers: "",
        following: "",
        created_at: "",
        updated_at: "",
      },
    };
  },
  methods: {
    getUser() {
      User.listar(this.user.login).then((response) => {
        this.user = response.data;
      });
    },
  },
};
</script>