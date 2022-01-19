<template>
  <div class="new-docs-banner">
    <div class="new-docs-banner__warning">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M23 21L12 2L1 21H23ZM11 18V16H13V18H11ZM11 14H13V10H11V14Z" fill="#FFC805"/>
      </svg>
    </div>
    <p>
      <b>You are viewing the v1 Nacelle Docs for existing merchants.</b>New merchants can find the V2 docs here: <a href="https://nacelle.com/docs/">nacelle.com/docs</a>.
    </p>
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
  background: #4464cc;
  color: white;
  padding: 1.5rem 1rem;
  display: flex;
  align-items: center;
  justify-content: center;

  p {
    margin: 0;
  }

  a {
    color: white;
    text-decoration: underline;

    &:hover {
      text-decoration: none;
    }
  }

  .new-docs-banner__warning {
    margin-right: 10px;
  }
}
</style>
