<template>
  <div class="row container">
  <app-header></app-header>
  <app-main></app-main>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  name:'app',
  components:{AppHeader, AppMain},
};
</script>

<style>
</style>
