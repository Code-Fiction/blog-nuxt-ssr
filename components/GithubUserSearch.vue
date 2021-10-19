<template>
  <div>{{ user }}</div>
</template>

<script>
export default {
  name: "GithubUserSearch",
  props: {
    userName: {
      type: String,
      required: true
    }
  },
  data: () => ({
    user: null
  }),
  // Request for get a user
  async fetch() {
    const userName = this.$props.userName || null;

    this.user = await this.$axios
      .get(`https://api.github.com/users/${userName}`)
      .then(response => response.data)
      .catch(() => null);
  }
};
</script>

<style scoped></style>
