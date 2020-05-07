<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/statistics">Statistics</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
  export default {
    data() {
      return {

      }
    }
  }
</script>

<style src="../src/assets/scss/app.scss" lang="scss"></style>
