<template>
  <v-app class="app__wrapper">
    <video
      :src="require('@/assets/video/beach.mp4')"
      width="1920"
      height="1080"
      muted
      loop
      autoplay
      class="app__video-background"
      type="video/mp4"
      playsinline
      preload
      pip="false"
    />
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
<style lang="scss">
.app {
  &__wrapper {
    position: relative;
  }

  &__video-background {
    position: absolute;
    object-fit: cover;
  }
}
</style>
