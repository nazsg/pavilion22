<template>
  <div>
    <ul>
      <li><nuxt-link to="/">Home</nuxt-link></li>
      <li><nuxt-link to="/other">Other</nuxt-link></li>
    </ul>
  </div>
</template>

<script>
export default {}
</script>

<style>
ul {
  display: flex;
  justify-content: space-around;
  list-style-type: none;
}
</style>
