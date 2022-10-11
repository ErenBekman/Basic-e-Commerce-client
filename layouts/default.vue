<template>
  <v-app dark :style="{ backgroundColor: $vuetify.theme.dark ? '#0a0514' : 'white' }">
    <Nav />
    <v-main>
      <Nuxt />
    </v-main>

    <Footer />
    <ScrollTop />
  </v-app>
</template>

<script>
export default {};
</script>
