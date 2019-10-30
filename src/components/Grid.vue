<template>
  <div class="grid">
    <header class="header">
      <slot name="header" />
    </header>
    <aside class="aside">
      <slot name="aside" />
    </aside>
    <main class="main">
      <slot name="main" />
    </main>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend()
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 50px calc(100vh - 50px);
}
.header {
  grid-column: 1/2;
  grid-row: 1/2;
  background-color: #FAA;
}
.aside {
  grid-column: 1/2;
  grid-row: 2/3;
}
.main {
  grid-column: 1/2;
  grid-row: 2/3;
  background-color: #AAF;
}
</style>
