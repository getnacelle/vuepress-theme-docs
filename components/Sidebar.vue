<template>
  <aside class="sidebar">
    <NavLinks />

    <slot name="top" />

    <SidebarLinks :depth="0" :items="items" />
    <slot name="bottom" />
  </aside>
</template>

<script>
import SidebarLinks from '@parent-theme/components/SidebarLinks.vue';
import NavLinks from '@parent-theme/components/NavLinks.vue';

export default {
  name: 'Sidebar',
  components: {
    SidebarLinks,
    NavLinks
  },
  props: ['items']
};
</script>

<style lang="stylus">
@require '../styles/palette.styl';

.page {
  padding-left: 436px;
}

.sidebar {
  top: 85px;
  width: 436px;

  .sidebar-links {
    padding-right: 6
  }

  .sidebar-heading {
    font-size: 24px;
    line-height: 40px;
    letter-spacing: 0.75px;
    padding-bottom: 10px;
    padding-top: 0;
    padding-left: 56px;
  }

  .sidebar-group a.sidebar-link.active {
    padding-bottom: 6px;
  }

  .sidebar-sub-headers a.sidebar-link.active {
    padding-bottom: 2px;
  }

  .sidebar-group a.sidebar-link,
  .sidebar-group.is-sub-group > .sidebar-heading,
  .sidebar-group.is-sub-group > .sidebar-group-items > li > .sidebar-link {
    font-size: 18px;
    line-height: 36px;
    letter-spacing: 0.56px;
  }

  .sidebar-sub-headers a.sidebar-link {
    padding-left: 67px;
  }

  .sidebar-group a.sidebar-link {
    padding-left: 67px;
    padding-top: 2px;
    padding-bottom: 2px;
  }

  .sidebar-group.is-sub-group > .sidebar-group-items > li > .sidebar-link {
    padding-top: 2px;
    padding-bottom: 2px;
    padding-left: 77px;
  }

  .sidebar-group.is-sub-group > .sidebar-heading:not(.clickable) {
    opacity: 1;
    padding-left: 71px;
  }

  .sidebar-group.is-sub-group > .sidebar-heading:not(.clickable).open {
    color: $accentColor;
    font-weight: 700;
    padding-bottom: 6px;
  }

  .sidebar-group.is-sub-group > .sidebar-heading:not(.clickable):hover {
    color: $accentColor;
  }

  .sidebar-group.is-sub-group > .sidebar-group-items {
    padding-bottom: 20px;
  }

  .arrow.right {
    border-left: 4px solid $accentColor;
  }

  .arrow.down {
    border-top: 4px solid $accentColor;
  }
}

@media (max-width: $MQNarrow) {
  .sidebar {
    top: 0;
    padding-top: 3.6rem;
    transform: translateX(-100%);
    transition: transform .2s ease;
  }

  .page {
    padding-left: 0;
  }
}
</style>
