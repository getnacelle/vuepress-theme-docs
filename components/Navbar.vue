<template>
  <header class="navbar">
    <SidebarButton @toggle-sidebar="$emit('toggle-sidebar')" />

    <RouterLink :to="$localePath" class="home-link">
      <div class="site-logo-layout">
        <img
          v-if="$site.themeConfig.logo"
          class="logo"
          :src="$withBase($site.themeConfig.logo)"
          :alt="$siteTitle"
        />
        <p v-if="$siteTitle" ref="siteName" class="site-name">
          {{ companyName }}
          <span v-if="$siteTitle" class="site-type">{{ siteType }}</span>
        </p>
      </div>
    </RouterLink>

    <div
      class="links"
      :style="
        linksWrapMaxWidth
          ? {
              'max-width': linksWrapMaxWidth + 'px'
            }
          : {}
      "
    >
      <SearchBox
        v-if="
          $site.themeConfig.search !== false &&
          $page.frontmatter.search !== false
        "
      />
      <NavLinks class="can-hide" />
    </div>
  </header>
</template>

<script>
import SearchBox from '@SearchBox';
import SidebarButton from '@parent-theme/components/SidebarButton.vue';
import NavLinks from '@parent-theme/components/NavLinks.vue';
export default {
  name: 'Navbar',
  components: {
    SidebarButton,
    NavLinks,
    SearchBox
  },
  data() {
    return {
      linksWrapMaxWidth: null
    };
  },
  computed: {
    companyName() {
      const [name] = this.$siteTitle.split(' ');
      return name.toUpperCase();
    },
    siteType() {
      const [, type] = this.$siteTitle.split(' ');
      return type.toUpperCase();
    }
  },
  mounted() {
    const MOBILE_DESKTOP_BREAKPOINT = 719; // refer to config.styl
    const NAVBAR_VERTICAL_PADDING =
      parseInt(css(this.$el, 'paddingLeft')) +
      parseInt(css(this.$el, 'paddingRight'));
    const handleLinksWrapWidth = () => {
      if (document.documentElement.clientWidth < MOBILE_DESKTOP_BREAKPOINT) {
        this.linksWrapMaxWidth = null;
      } else {
        this.linksWrapMaxWidth =
          this.$el.offsetWidth -
          NAVBAR_VERTICAL_PADDING -
          ((this.$refs.siteName && this.$refs.siteName.offsetWidth) || 0);
      }
    };
    handleLinksWrapWidth();
    window.addEventListener('resize', handleLinksWrapWidth, false);
  }
};
function css(el, property) {
  // NOTE: Known bug, will return 'auto' if style value is 'auto'
  const win = el.ownerDocument.defaultView;
  // null means not to return pseudo styles
  return win.getComputedStyle(el, null)[property];
}
</script>

<style lang="stylus">
@require '../styles/palette.styl';

.sidebar-button {
  padding: 22px 24px;
}

.navbar {
  padding: 25px 56px;
  line-height: 20px;
  height: auto;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

  a,
  span,
  img {
    display: inline-block;
  }

  .logo {
    height: auto;
    width: 30px;
    margin-right: 0.8rem;
    vertical-align: top;
  }

  .site-logo-layout {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  .site-name {
    font-size: 1.3rem;
    font-weight: 700;
    color: $textColor;
    position: relative;
    margin: 0;
  }

  .site-type {
    color: $secondaryColor;
    margin-left: 2px;
  }

  .links {
    position: static;
    padding-left: 1.5rem;
    box-sizing: border-box;
    background-color: $white;
    white-space: nowrap;
    font-size: 0.9rem;
    display: flex;
  }
}

.search-box input {
  width: 14rem;
}

.nav-links {
  display: flex;
  align-items: center;
  a {
    font-size: 15px;
    line-height: 20px;
    padding-left: 0;
  }
}

@media (max-width: $MQNarrow) {
  .search-box input {
    width: 0;
  }

  .navbar {
    padding: 25px 40px;

    a {
      padding-left: 42px;
    }
  }

  .sidebar-button {
    display: block;
  }
}

@media (max-width: 560px) {
  .navbar .logo {
    display: none;
  }
}

@media (max-width: 468px) {
  .navbar .site-type {
    display: none;
  }
}

@media (max-width: $MQMobile) {
  .can-hide {
    display: none;
  }
}
</style>
