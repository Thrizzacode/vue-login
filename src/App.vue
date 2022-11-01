<script setup>
import { RouterLink, RouterView } from 'vue-router'
console.log(import.meta.env.VITE_APP_API, import.meta.env.VITE_APP_PATH);
</script>

<template>
  <div>

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/login">Login</RouterLink>
    </nav>

  </div>

  <RouterView />
</template>

<style lang="scss">

</style>

