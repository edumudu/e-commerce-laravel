<template>
  <div class="tabs-wrapper">
    <ul class="tabs">
      <li
        v-for="tab in tabs"
        :key="tab.index"
        :class="{ active: tab.isActive }"
      >
        <a
          :href="tab.href"
          data-toggle="tab"
          @click.prevent="selectTab(tab)"
        >
          {{ tab.name }}
        </a>
      </li>
    </ul>

    <div class="tab-content">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    tabs: [],
  }),

  created () {
    this.tabs = this.$children;
  },

  methods: {
    selectTab (selectedTab) {
      this.tabs.forEach((tab) => {
        tab.isActive = tab.name === selectedTab.name;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '~/assets/scss/components/_tabs';
</style>
