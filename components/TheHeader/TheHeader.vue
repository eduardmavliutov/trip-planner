<template>
  <header class="header">
    <v-navigation-drawer
      v-model="drawer"
      temporary
      floating
      app
      class="header__nav"
    >
      <template #img>
        <v-img
          :src="require('../../assets/images/beach.jpeg')"
          class="header__nav-image"
        />
      </template>
      <v-list
        class="header__nav-list"
        rounded
        nav
      >
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
          class="header__nav-list-item"
        >
          <v-list-item-action>
            <v-icon>
              {{ item.icon }}
            </v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      class="header__bar"
      clipped-left
      fixed
      dark
      app
    >
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-toolbar-title
        class="header__nav-title"
        v-text="title"
      />
      <v-spacer />
    </v-app-bar>
  </header>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({})
export default class TheHeader extends Vue {
  private drawer = false
  private title = 'Trip Planner'
  private items = [
    {
      icon: 'mdi-palm-tree',
      title: 'Home page',
      to: '/'
    },
    {
      icon: 'mdi-chart-bubble',
      title: 'About',
      to: '/about'
    }
  ]
}
</script>
<style lang="scss">
.header {
  &__nav {
    margin: 2vh;
    max-height: 96vh;

    @media (max-width: 768px) {
      margin: 0;
      max-height: unset;
    }

    &-title {
      font-weight: 600;
    }

    &-list-item {
      color: $color-white;
      font-weight: 500;
    }

    &-image {
      position: relative;
      height: 100%;

      &::before {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(255, 255, 255, 0.7);
        content: "";
      }
    }
  }

  &__bar {
    background-color: $color-green--main;
  }
}

</style>
