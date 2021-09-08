<template>
  <div class="banner">
    <transition name="slide">
      <div class="banner-container" v-if="open">
        <p>{{ message }}</p>
        <nacelle-button
          class="nacelle-banner-button"
          @click="goTo(buttonPath)"
          color="secondary"
          >{{ buttonText }}</nacelle-button
        >
        <img
          @click="closeBanner"
          class="close-banner"
          src="/alertbar-x-icon.svg"
        />
      </div>
    </transition>
  </div>
</template>

<script>
import NacelleButton from './NacelleButton.vue'
export default {
  components: {
    NacelleButton
  },
  data() {
    return {
      open: false
    }
  },
  props: {
    title: {
      type: String,
      default: ''
    },
    buttonText: {
      type: String,
      default: ''
    },
    buttonPath: {
      type: String,
      default: ''
    },
    message: {
      type: String,
      default: ''
    }
  },
  mounted() {
    setTimeout(() => {
      this.open = true
    }, 1000)
  },
  methods: {
    goTo(path) {
      window.open(path, '_blank')
    },
    closeBanner() {
      this.open = false
    }
  }
}
</script>

<style lang="scss" scoped>
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter-to,
.slide-leave {
  transform: translateY(0px);
}

.slide-enter,
.slide-leave-to {
  transform: translateY(100px);
}

.banner-container {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100vw;
  height: 80px;
  background: #00baff;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
  p {
    font-weight: 700;
    text-align: center;
    margin-right: 50px;
    color: white;
    font-family: "HK Grotesk";
    font-size: 18px;
    letter-spacing: .39px;
    line-height: 26px;
  }
  .close-banner {
    cursor: pointer;
    height: 15px;
    filter: brightness(0) invert(1);
    position: absolute;
    right: 40px;
  }
}

@media screen and (max-width: 1023px) {
  .banner-container {
    flex-direction: column;
    height: 110px;
    // align-items: flex-start;

    .nacelle-banner-button {
      margin-left: 20px;
    }
    p {
      margin: 0 20px 6px;
      font-size: 16px;
      letter-spacing: .25px;
      line-height: 24px;
      // text-align: left;
    }
    .close-banner {
      right: 20px;
      bottom: 20px;
    }
  }
}
</style>
