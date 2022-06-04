<template>
  <router-view></router-view>
</template>

<style lang="scss">
// Main Stylesheet
@import './src/assets/scss/main';

// Bootstrap Vue Stylesheet
@import '~bootstrap-vue/src/index';

// All color themes are included and available by default
// Feel free to comment out any of them if you won't use them in your project
@import './src/assets/scss/oneui/themes/amethyst';
@import './src/assets/scss/oneui/themes/city';
@import './src/assets/scss/oneui/themes/flat';
@import './src/assets/scss/oneui/themes/modern';
@import './src/assets/scss/oneui/themes/smooth';
</style>

<script>
import {mapActions, mapState} from 'vuex';

export default {
  name: 'App',
  computed: {
    ...mapState({
      token: "token"
    })
  },
  created() {
    const user = localStorage.getItem("user");
    this.updateCurrentUser(JSON.parse(user))
  },
  methods: {
    ...mapActions({
      setToken: "setToken"
    }),
    ...mapActions("authentication",{
      updateCurrentUser:"updateCurrentUser"
    })
  }
}
</script>
