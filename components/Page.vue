<template>
  <main class="page">
    <slot name="top" />

    <Content class="theme-default-content" />
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
    <Footer />

    <Banner v-if="$page.bannerData" v-bind="$page.bannerData" />
  </main>
</template>

<script>
import PageEdit from '@parent-theme/components/PageEdit.vue';
import PageNav from '@parent-theme/components/PageNav.vue';
import Footer from './Footer.vue';
import Banner from './Banner.vue';

export default {
  components: { PageEdit, PageNav, Footer, Banner },
  props: ['sidebarItems']
};
</script>
