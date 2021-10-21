<template>
  <div class="home">
    <h2>
      Using Nuxt with Server-Side Rendering
    </h2>
    <div class="home-links">
      <a href="/fetch/adjonata">Using Fetch</a>
      <a href="/async-data/adjonata">Using Async Data</a>
    </div>
  </div>
</template>

<style>
.home {
  width: 100%;
  padding: 50px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-family: sans-serif;
}
.home h2 {
  color: #363636;
}
.home-links {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.home-links a {
  text-decoration: none;
  font-weight: 600;
  line-height: 30px;
  margin-bottom: 10px;
}
</style>
