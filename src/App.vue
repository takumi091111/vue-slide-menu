<template>
  <grid>
    <template #header>
      <v-header>
        <button @click="toggleOpen">≡</button>
      </v-header>
    </template>
    <template #aside>
      <slide-menu :is-open="isOpen" @outer-click="toggleOpen">
        <ul>
          <li>A</li>
          <li>B</li>
          <li>C</li>
        </ul>
      </slide-menu>
    </template>
    <template #main>
      <p>Main</p>
    </template>
  </grid>
</template>

<script lang="ts">
import Vue from 'vue'
import Grid from '~/components/Grid.vue'
import Header from '~/components/Header.vue'
import SlideMenu from '~/components/SlideMenu.vue'
export default Vue.extend({
  components: {
    Grid,
    SlideMenu,
    'v-header': Header,
  },
  data() {
    return {
      isOpen: null as boolean | null
    }
  },
  methods: {
    toggleOpen() {
      this.isOpen = this.isOpen === null ? true : !this.isOpen
    }
  }
})
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
}
</style>
