<template>
  <div id="app">
    <ProfileInfo />
  </div>
</template>

<script>
import ProfileInfo from './components/ProfileInfo.vue'
export default {
  name: 'app',
  components: {
    ProfileInfo
  }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;

  text-align: center;
  color: #2c3c4b;
  margin-top: 40px;
}
</style>