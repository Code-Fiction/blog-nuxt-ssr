<template>
  <div class="github-user">
    <GithubUser v-if="userData" :user-data="userData" />
  </div>
</template>

<script>
import GithubUser from "@/components/GithubUser.vue";

export default {
  components: {
    GithubUser
  },
  // Request for get a user
  async asyncData({ $axios, params }) {
    const { user = null } = params;

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
      title: this.userData?.name || "Github user"
    };
  }
};
</script>

<style scoped></style>
