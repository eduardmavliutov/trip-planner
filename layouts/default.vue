<template>
  <v-app>
    <the-header />
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import TheHeader from '@/components/TheHeader/TheHeader.vue'

@Component({
  components: {
    TheHeader
  }
})
export default class LayoutDefault extends Vue {
}
</script>
