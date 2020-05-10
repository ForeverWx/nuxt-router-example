<template>
  <div>
    <h1>菜单</h1>
    <el-row>
      <el-col :span="12">
        <ul>
          <li>
            <nuxt-link to="/example/home/home_menu/index">index</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/example/home/home_menu/blog">blog</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/example/home/home_menu/college">colleage</nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col :span="12">
        <nuxt-child/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: "home_vue"
  }
</script>

<style scoped>

</style>
