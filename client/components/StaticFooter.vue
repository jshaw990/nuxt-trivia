<template>
  <div>
    <v-footer v-if="$vuetify.breakpoint.mdAndUp">
      <v-row class="ma-4">
        <NuxtLink to="/">
          <v-icon>mdi-home</v-icon>
          <span>Home</span>
        </NuxtLink>
      </v-row>
    </v-footer>
    <v-col v-else  class="ma-4">
      <NuxtLink to="/">
        <v-icon>mdi-home</v-icon>
        <span>Home</span>
      </NuxtLink>
    </v-col>
  </div>
</template>

<script>
export default {
  name: 'StaticFooter'
}
</script>
