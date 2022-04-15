<template>
  <v-app>
    <the-header />
    <nuxt />
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
export default class MainDefault extends Vue {
}
</script>
