<template>
  <v-main>
    <h1>
      Auth will be here
    </h1>
  </v-main>
</template>
<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

@Component({
  layout: 'main',
  transition: 'route-change-right'
})
export default class AuthPage extends Vue {

}
</script>
