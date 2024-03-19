<template>
  <div class="felx flex-col min-h-screen font-Roboto bg-weather-primary">
    <SiteNavigation />
    <RouterView />
  </div>
</template>

<script>
import SiteNavigation from './components/SiteNavigation.vue';

  export default {
    components: { SiteNavigation }
}
</script>

<style lang="scss" scoped>

</style>