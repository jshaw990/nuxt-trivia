<template>
  <v-app dark>
    <StaticHeader />
    <v-main class="ma-2">
      <Nuxt />
    </v-main>
    <StaticFooter />
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout'
}
</script>
