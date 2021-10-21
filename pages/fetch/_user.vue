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
  data: () => ({
    userData: null
  }),
  async fetch() {
    const { user = null } = this.$route.params;

    if (!user) return;

    this.userData = await this.$axios
      .get(`https://api.github.com/users/${user}`)
      .then(response => response.data)
      .catch(() => null);
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
