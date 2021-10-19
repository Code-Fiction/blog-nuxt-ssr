<template>
  <div class="github-user">
    <GithubUser v-if="userData" :user-data="userData" />
    <p class="notfound" v-else>User not found</p>
  </div>
</template>

<script>
import GithubUser from "@/components/GithubUser.vue";

export default {
  components: { GithubUser },
  async asyncData({ $axios, params }) {
    // User name from route params
    const { user = null } = params;

    // Request for get a user
    const userData = await $axios
      .get(`https://api.github.com/users/${user}`)
      .then(response => response.data)
      .catch(() => null);

    return {
      userData
    };
  },
  // Customize head title
  head() {
    return {
      title: this.userData.name || "Github user"
    };
  }
};
</script>

<style scoped></style>
