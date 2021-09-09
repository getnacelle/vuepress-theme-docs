<template>
  <div :class="block ? 'block' : null" class="nacelle-button">
    <a :class="color" :href="buttonPath" target="_blank">
      <span>
        <slot />
      </span>
      <template v-if="!noIcon">
        <div v-if="icon" v-html="icon" class="nacelle-button-icon"></div>
        <img v-else src="/nacelle-arrow-right.svg" alt="arrow-right" />
      </template>
    </a>
  </div>
</template>

<script>
export default {
  props: {
    buttonPath: {
      type: String,
      default: null
    },
    external: {
      type: Boolean,
      default: false
    },
    color: {
      type: String,
      default: 'primary'
    },
    icon: {
      type: String,
      default: null
    },
    noIcon: {
      type: Boolean,
      default: false
    },
    block: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    clickHandler() {
      if (this.buttonPath) {
        window.open(this.buttonPath, '_blank')
      } else {
        this.$emit('click')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.nacelle-button {
  display: inline-block;
  margin: 5px;

  &.block {
    display: flex;
    justify-content: center;

    button {
      justify-content: center;
      max-width: 600px;
    }
  }
}
a {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-decoration: none;
  border: 2px solid #00baff;
  border-radius: 5px;
  padding: 10px 14px;
  font-size: 16px;
  width: 100%;
  background: none;
  cursor: pointer;
  transition: all 0.3s;

  span {
    color: #ffffff;
    font-family: 'HK Grotesk';
    font-size: 16px;
    font-weight: bold;
    letter-spacing: 0.44px;
    line-height: 20px;
  }
  img {
    margin-left: 24px;
    filter: invert(58%) sepia(35%) saturate(4655%) hue-rotate(162deg)
      brightness(102%) contrast(104%); //Makes color #00BAFF (Blue)
  }
  &:hover {
    background: #22346b;
  }
}
.secondary {
  border: 2px solid #fff;
  img {
    filter: brightness(0) invert(1);
  }
  &:hover {
    border: 2px solid #00baff;
    span {
      color: #00baff;
    }
    img {
      filter: invert(58%) sepia(35%) saturate(4655%) hue-rotate(162deg)
        brightness(102%) contrast(104%); //Makes color #00BAFF (Blue)
    }
    background: #fff;
  }
}

// mobile
@media screen and (max-width: 1023px) {
  button {
    border-radius: 5px;
    padding: 4px 8px;
    span {
      font-size: 16px;
      letter-spacing: 0.25px;
      line-height: 24px;
    }
    img {
      width: 15px;
    }
  }
}
</style>
