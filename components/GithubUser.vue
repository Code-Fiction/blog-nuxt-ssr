<template>
  <div class="user">
    <img class="user-image" :src="userData.avatar_url" alt="User avatar" />

    <div class="user-infos">
      <h1 @click="goToGithubProfile()">{{ userData.name }}</h1>
      <h2 v-if="userData.bio">{{ userData.bio }}</h2>
      <span>Registration date: {{ userData.created_at.substring(0, 10) }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "GithubUser",
  props: {
    // Github user data
    userData: {
      required: true,
      type: Object
    }
  },
  methods: {
    goToGithubProfile() {
      window.location = this.userData.html_url;
    }
  }
};
</script>

<style scoped>
.user {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.user-image {
  width: 200px;
  border: solid 3px #3574d3;
  border-radius: 20px;
}

.user-infos {
  text-align: center;
  font-family: sans-serif;
  color: #353535;
}

.user-infos h1 {
  cursor: pointer;
}
.user-infos h2 {
  color: #505050;
  font-weight: 400;
}
.user-infos b {
  font-weight: 300;
}
</style>
