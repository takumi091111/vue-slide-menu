<template>
  <div :class="panelClass">
    <div :class="outerClass" @click="handleOuterClick"></div>
    <nav :class="innerClass">
      <slot />
    </nav>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    isOpen: {
      type: Boolean || null,
      required: false,
      default: null
    }
  },
  computed: {
    panelClass(): string {
      return ['slide-panel', this.isOpen ? '' : 'hide']
        .join(' ').trim()
    },
    outerClass(): string {
      if (this.isOpen === null) return 'outer'
      return ['outer', this.isOpen ? 'fadeIn' : 'fadeOut']
        .join(' ')
    },
    innerClass(): string {
      if (this.isOpen === null) return 'inner'
      return ['inner', this.isOpen ? 'slideIn' : 'slideOut']
        .join(' ')
    }
  },
  methods: {
    handleOuterClick() {
      this.$emit('outer-click')
    }
  }
})
</script>

<style scoped>
.slide-panel {
  position: absolute;
  top: 50px;
  left: 0;
  width: 100vw;
  height: calc(100vh - 50px);
  z-index: 0;
}
.outer {
  background-color: #AAA;
  position: fixed;
  width: 100%;
  height: 100%;
  transition-timing-function: cubic-bezier(0.645, 0.045, 0.355, 1);
  transition-duration: 0.5s;
  opacity: 0;
}
.inner {
  background-color: #AFA;
  position: fixed;
  right: -400px;
  width: 400px;
  height: 100%;
  transition-timing-function: cubic-bezier(0.645, 0.045, 0.355, 1);
  transition-duration: 0.5s;
}
.hide {
  transition-delay: 0.5s;
  z-index: -1;
}
.fadeIn {
  opacity: 0.8;
}
.fadeOut {
  opacity: 0;
}
.slideIn {
  transform: translateX(-400px);
}
.slideOut {
  transform: translateX(0);
}
</style>
