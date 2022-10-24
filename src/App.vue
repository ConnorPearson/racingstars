<template>
  <div id="app">
    <ProfileInfo />
  </div>
</template>

<script>
import ProfileInfo from './ProfileInfo.vue'
export default {
  name: 'app',
  components: {
    ProfileInfo
  }
}
</script>

<style>
#app {
  font-family: Inter var,ui-sans-serif,system-ui,-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica Neue,Arial,Noto Sans,sans-serif,Apple Color Emoji,Segoe UI Emoji,Segoe UI Symbol,Noto Color Emoji;
 
  text-align: center;
  color: #2c3c4b;
}
</style>