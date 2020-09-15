<template>
  <main class="home" aria-labelledby="main-title">
    <div class="content-container">
      <header class="hero">
        <h4 v-if="data.imageText" class="image-text">{{ data.imageText }}</h4>
        <a v-if="data.heroImage" :href="$withBase(data.heroImageLink || '')">
          <img
            v-if="data.heroImage"
            :src="$withBase(data.heroImage)"
            :alt="data.heroAlt || 'hero'"
          />
        </a>
      </header>
      <Content class="theme-default-content custom" />

      <div class="start-layout">
        <Content slot-key="quick-start" />
        <Content slot-key="get-started" />
      </div>
    </div>
    <Footer />
  </main>
</template>

<script>
import Footer from './Footer.vue';

export default {
  name: 'Home',
  components: { Footer },
  computed: {
    data() {
      return this.$page.frontmatter;
    }
  }
};
</script>

<style lang="stylus">
@require '../styles/palette.styl';

.home {
  display: block;

  .content-container {
    margin: 0px auto;
    padding: 226px 2rem 0;
    max-width: 770px;
  }

  .hero {
    text-align: center;

    .image-text {
      font-size: 14px;
      line-height: 18px;
      color: $secondaryColor;
      font-weight: 400;
      margin: 0;
    }

    img {
      max-width: 100%;
      max-height: 360px;
      display: block;
      margin: 3rem auto 1.5rem;
      margin-top: 19px;
    }
  }

  .start-layout {
    display: flex;
    flex-direction: row;
  }

  .content__quick-start,
  .content__get-started {
    display: flex;
    flex-direction: column;
    width: 50%;

    h2 {
      font-weight: 400;
      margin-bottom: 11px;
      margin-top: 31px;
    }

    p {
      margin-top: 0;
      margin-bottom: 6px;
    }

    p a {
      font-weight: 700;
    }
  }

  .content__quick-start {
    margin-right: 15px;
  }

  .content__get-started {
    margin-left: 15px;
  }
}

@media (max-width: $MQMobile) {
  .home {
    .start-layout {
      flex-direction: column;
    }

    .content__quick-start,
    .content__get-started {
      width: 100%;
    }

    .content__quick-start {
      margin-right: 0;
    }

    .content__get-started {
      margin-left: 0;
    }
  }
}

@media (min-width: 420px) and (max-width: $MQMobile) {
  .home .content-container  {
    padding: 145px 2rem 0;
  }
}

@media (max-width: $MQMobileNarrow) {
  .home {
    .content-container  {
      padding: 117px 2rem 0;
    }

    .hero {
      img {
        max-height: 210px;
        margin: 2rem auto 1.2rem;
      }

      h1 {
        font-size: 2rem;
      }

      h1, .description {
        margin: 1.2rem auto;
      }

      .description {
        font-size: 1.2rem;
      }

    }
  }
}
</style>
