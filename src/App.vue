<template>
  <header>
    <AppHeader></AppHeader>
  </header>
  <main>
    <div class="container">
      <router-view></router-view>
    </div>
  </main>
</template>

<script>
import AppHeader from './components/HeaderComponent.vue';
export default {
  name: 'App',
  components: {
    AppHeader
  }
}
</script>

<style lang="scss" scoped>

</style>