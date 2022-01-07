<template>
  <div class="new-docs-banner">
    <div>⚠️</div>
    <p>
      You are viewing the v1 Nacelle Docs.<br />
      For the newest updates, visit <a href="https://nacelle.com/docs/">nacelle.com/docs</a>.
    </p>
    <div>
      ⚠️
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    // get the height of the element with class '.navbar'
    const navbarHeight = document.querySelector('.navbar').offsetHeight;
    // set the top css attribute to the navbarHeight
    document.querySelector('.new-docs-banner').style.marginTop = navbarHeight + 'px';
  }
}
</script>

<style lang="scss" scoped>
.new-docs-banner {
  height: auto;
  /* background: rgba(221, 15, 23, 0.2);
  border-bottom: 1px solid rgb(221, 15, 23); */
  background: #4464cc;
  color: white;
  padding: 1.5rem 1rem;
  display: flex;
  align-items: center;
  justify-content: center;

  p {
    margin: 0 1.5rem;
    text-align: center;
  }

  a {
    color: white;
    text-decoration: underline;

    &:hover {
      text-decoration: none;
    }
  }
}
</style>
