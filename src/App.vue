<template>
  <v-app>
    <v-main>
      <Header />
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  component:{
    Header
  },
  data: () => ({
    //
  }),
};
</script>

<style scoped>
#app {
  background-image: linear-gradient(to right, #ffffff, #d8d8d8);
}
</style>
