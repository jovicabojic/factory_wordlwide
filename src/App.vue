<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">Statistics</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style src="../src/assets/scss/app.scss" lang="scss"></style>
