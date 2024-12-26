<script>
import AppHeader from './components/AppHeader.vue';
export default {
  components: {
    AppHeader
  }
}
</script>

<template>
  <AppHeader />
  <router-view/>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
</style>
