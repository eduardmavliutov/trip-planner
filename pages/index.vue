<template>
  <v-main class="page page--main">
    <v-container class="page__container">
      <h1 class="page__title">
        Trip Planner
      </h1>
      <ul class="page__actions-list">
        <li class="page__actions-list-item">
          <p class="page__actions-list-action-text">
            &#128198; Plan
          </p>
        </li>
        <li class="page__actions-list-item">
          <p class="page__actions-list-action-text">
            &#128241; Calculate
          </p>
        </li>
        <li class="page__actions-list-item">
          <p class="page__actions-list-action-text">
            &#127965; Travel
          </p>
        </li>
      </ul>
      <nuxt-link :to="{ name: 'auth' }" class="page__auth-link">
        Plan your next trip
      </nuxt-link>
    </v-container>
  </v-main>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import { gsap } from 'gsap'

// TODO add webm video files
@Component({
  layout: 'main'
})
export default class MainPage extends Vue {
  private timeline!: gsap.core.Timeline

  mounted () {
    this.timeline = gsap.timeline()
    this.timeline.to('.page__title', {
      borderWidth: 10,
      duration: 0.3
    })
    this.timeline.fromTo('.page__actions-list-item', {
      opacity: 0,
      translateX: '-10%'
    }, {
      translateX: '0%',
      duration: 0.5,
      opacity: 1,
      stagger: 0.3,
      ease: 'power1.out'
    }, '>')
  }
}
</script>
<style lang="scss">
.page {
  &--main {
    z-index: 1;
    max-height: 100vh;
    color: $color-white;
    overflow: hidden;
  }

  &__container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    @media screen and (max-width: 768px) {
      align-items: center;
    }
  }

  &__title {
    margin: 25px 0 40px 0;

    font-size: 60px;
    white-space: nowrap;
    border-bottom: 0 solid $color-green--main;
    text-shadow: 0px 0px 10px rgba(128, 128, 128, 0.397);

    @media screen and (max-width: 768px) {
      margin-top: 0;
    }
  }

  &__video {
    object-fit: cover;
  }

  &__actions-list {
    margin: 0 0 60px -24px;
    padding: 0;

    display: flex;
    flex-direction: column;
    align-items: flex-start;

    list-style-type: none;

    &-action-text {
      margin: 0;
      font-size: 50px;
      font-weight: bold;

      background: linear-gradient(to right, transparent 20%, rgba(128, 128, 128, 0.19) 80%, transparent 95%);
    }
  }

  &__auth-link {
    padding: 10px 20px;

    display: block;
    width: fit-content;

    font-size: 20px;
    font-weight: 600;
    text-decoration: none;
    text-transform: uppercase;
    color: $color-white !important; // to override vuetify's link's color
    white-space: nowrap;

    border-radius: 10px;
    background-color: $color-green--main;

    transition: 0.2s all ease-out;

    &:hover {
      transform: scale(1.1);
    }

    &:focus {
      transform: scale(1.1);
      outline: none;
      box-shadow: 0 0 4px 5px $color-white;
    }

    &:active {
      transform: scale(1.1);
      box-shadow: 0 0 4px 5px $color-white;
    }
  }
}
</style>
