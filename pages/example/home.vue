<template>
  <div>
    <h1>首页</h1>
    <div>
      <nuxt-link to="/example/home/index">index</nuxt-link>
      <nuxt-link to="/example/home/blog">blog</nuxt-link>
      <nuxt-link to="/example/home/college">colleage</nuxt-link>
      <nuxt-link to="/example/home/home_menu">menu</nuxt-link>
    </div>
    <div>
      <nuxt-child/>
    </div>
  </div>
</template>

<script>
  export default {
    name: "home.vue"
  }
</script>

<style scoped>

</style>
