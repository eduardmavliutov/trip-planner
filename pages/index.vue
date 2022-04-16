<template>
  <v-main class="page--main">
    <video
      :src="require('@/assets/video/beach.mp4')"
      width="1920"
      height="1080"
      muted
      loop
      autoplay
      class="page__video"
      type="video/mp4"
    />
  </v-main>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

// TODO add webm video files
@Component({
  layout: 'main'
})
export default class MainPage extends Vue {

}
</script>
<style lang="scss">
.page--main {
  max-height: 100vh;
  overflow: hidden;
}

.page__video {
  object-fit: cover;
}
</style>
