<template>
  <main id="dashboard-page">
    <the-aside-dashboard />

    <div id="dashboard-page-content">
      <the-header-dashboard />

      <nuxt keep-alive :keep-alive-props="{ max: 5 }" />
    </div>
  </main>
</template>

<script>
import TheAsideDashboard from '~/components/dashboard/TheAsideDashboard.vue';
import TheHeaderDashboard from '~/components/dashboard/TheHeaderDashboard.vue';

export default {
  components: {
    TheAsideDashboard,
    TheHeaderDashboard,
  },

  middleware: ['auth', 'moderation'],
  layoutTransition: 'layout',

  head () {
    return { titleTemplate: `%s | Dashboard ${this.$config.appName}` };
  },
};
</script>

<style lang="scss" scoped>
  @import '~/assets/scss/page-components/dashboard-content';
</style>
