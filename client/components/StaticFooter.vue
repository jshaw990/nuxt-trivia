<template>
  <div>
    <v-footer v-if="$vuetify.breakpoint.mdAndUp">
      <v-row class="ma-4 text-center" justify="center" align="center">
        <NuxtLink to="/">
          <v-icon>mdi-home</v-icon>
          <div>Home</div>
        </NuxtLink>
      </v-row>
    </v-footer>
    <v-col v-else class="text-center">
      <NuxtLink to="/">
        <v-icon>mdi-home</v-icon>
      </NuxtLink>
    </v-col>
    <v-switch class="flex-end" inset @click="switchTheme" />
  </div>
</template>

<script>
import { reactive, toRefs } from '@vue/composition-api'

export default {
  name: 'StaticFooter',
  setup (props, context) {
    const state = reactive({
      dark: true
    })

    const switchTheme = () => {
      context.root.$vuetify.theme.dark = !context.root.$vuetify.theme.dark
      state.dark = context.root.$vuetify.theme.dark
    }

    return {
      switchTheme,
      ...toRefs(state)
    }
  }
}
</script>
