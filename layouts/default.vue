<template>
  <main id="page">
    <the-header-site />

    <nuxt keep-alive :keep-alive-props="{ max: 5 }" />

    <the-footer-site />
  </main>
</template>

<script>
import TheHeaderSite from '~/components/page-components/TheHeaderSite.vue';
import TheFooterSite from '~/components/page-components/TheFooterSite.vue';

export default {
  layoutTransition: 'layout',

  components: {
    TheHeaderSite,
    TheFooterSite,
  },

  head () {
    return { titleTemplate: `%s | ${this.$config.appName}` };
  },

  mounted () {
    // init cart
    this.$store.commit('cart/setCart', JSON.parse(localStorage.getItem('cart')) || []);
    this.$store.dispatch('cart/fetchProducts');
  },
};
</script>

<style lang="scss">
  @import '~assets/scss/app.scss';
</style>
