<template>
  <v-main class="page--main">
    <transition-group tag="div" name="fade" appear mode="out-in">
      <video
        v-if="activeSourceIndex === 0"
        :key="0"
        :src="require('@/assets/video/beach.mp4')"
        width="1920"
        height="1080"
        muted
        loop
        autoplay
        class="page__video"
      />
      <video
        v-if="activeSourceIndex === 1"
        :key="1"
        :src="require('@/assets/video/mountain.mp4')"
        width="1920"
        height="1080"
        muted
        loop
        autoplay
        class="page__video"
      />
      <video
        v-if="activeSourceIndex === 2"
        :key="2"
        :src="require('@/assets/video/snow.mp4')"
        width="1920"
        height="1080"
        muted
        loop
        autoplay
        class="page__video"
      />
    </transition-group>
  </v-main>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

// TODO add webm video files
@Component({
  layout: 'main'
})
export default class MainPage extends Vue {
  private activeSourceIndex = 0

  private videoVisible = true

  private interval!: NodeJS.Timeout

  private sources = [
    require('@/assets/video/beach.mp4'),
    require('@/assets/video/snow.mp4'),
    require('@/assets/video/mountain.mp4')
  ]

  private setUpInterval () {
    this.interval = setInterval(() => {
      this.videoVisible = false
      if (this.activeSourceIndex === this.sources.length - 1) {
        this.activeSourceIndex = 0
      } else {
        this.activeSourceIndex++
      }
      this.videoVisible = true
    }, 10000)
  }

  beforeRouteLeave() {
    clearInterval(this.interval)
  }

  created () {
    this.setUpInterval()
  }
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
