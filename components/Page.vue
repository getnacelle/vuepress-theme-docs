<template>
  <main class="page">
    <slot name="top" />

    <Content class="theme-default-content" />
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
    <Footer />
  </main>
</template>

<script>
import PageEdit from '@parent-theme/components/PageEdit.vue';
import PageNav from '@parent-theme/components/PageNav.vue';
import Footer from './Footer.vue';

export default {
  components: { PageEdit, PageNav, Footer },
  props: ['sidebarItems']
};
</script>
