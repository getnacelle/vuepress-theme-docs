<template>
  <footer>
    <div class="footer-layout">
      <div
        v-for="(menu, menuIdx) in navSections"
        :key="menuIdx"
        class="can-hide"
      >
        <section>
          <h5 class="menu-title">
            {{ menu.title }}
          </h5>
          <a
            v-for="(link, linkIdx) in menu.links"
            :key="linkIdx"
            :href="link.url"
            target="_blank"
            class="footer-link"
            >{{ link.title }}</a
          >
        </section>
      </div>
      <section>
        <img
          v-if="$site.themeConfig.logo"
          class="footer-logo"
          :src="$withBase($site.themeConfig.footerLogo)"
          :alt="$siteTitle"
        />
        <a
          v-for="(link, linkIdx) in legal.links"
          :key="linkIdx"
          :href="link.url"
          target="_blank"
          :class="['footer-link', 'legal-link']"
          >{{ link.title }}</a
        >
        <span id="copyright"> &copy; Nacelle {{ currentYear }} </span>
      </section>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data: () => ({
    currentYear: new Date().getFullYear(),
    navSections: [
      {
        title: 'Customers',
        links: [
          {
            title: 'For Merchants',
            url: 'https://www.getnacelle.com/headless-commerce-for-merchants',
          },
          {
            title: 'For Developers',
            url: 'https://www.getnacelle.com/jamstack-ecommerce-for-developers',
          },
          {
            title: 'For Agencies',
            url: 'https://www.getnacelle.com/headless-commerce-for-agencies',
          },
        ],
      },
      {
        title: 'Company',
        links: [
          {
            title: 'Team',
            path: 'https://www.getnacelle.com/team',
          },
          {
            title: 'Careers',
            path: 'https://www.getnacelle.com/team-and-careers',
          },
          {
            title: 'Partners',
            path: 'https://www.getnacelle.com/become-a-partner',
          },
          {
            title: 'Contact',
            path: 'https://www.getnacelle.com/contact-us',
          },
        ],
      },
      {
        title: 'Resources',
        links: [
          // Blog currently unvavailable on the website
          // We can add this back in when it's available
          // {
          //   title: 'Blog',
          //   path: 'https://www.getnacelle.com/blog',
          // },
          {
            title: 'FAQs',
            path: 'https://www.getnacelle.com/faqs',
          },
        ],
      },
    ],
    legal: {
      title: 'NACELLE',
      links: [
        {
          title: 'Privacy Policy',
          path: 'https://www.getnacelle.com/privacy-policy',
        },
        {
          title: 'Terms of Use',
          path: 'https://www.getnacelle.com/terms-and-conditions',
        },
      ],
    },
  }),
}
</script>

<style lang="stylus">
@require '../styles/palette.styl';

footer {
  background-color: $textColor;
  width: 100%;
  box-sizing: border-box;
  color: white;
  padding-top: 108px;
  padding-bottom: 77px;
  margin-top: 80px;

  section {
    display: flex;
    flex-direction: column;
  }

  .footer-layout {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-around;
    margin: 0 auto;
  }

  .menu-title {
    margin-top: 0;
    font-size: 22px;
    font-weight: bold;
    letter-spacing: 0.5px;
    line-height: 30px;
    margin-bottom: 7px;
  }

  .footer-link {
    color: white;
    font-weight: 700;
    text-decoration: none;
    width: fit-content;
    background-image: linear-gradient(to right, transparent 100%);
    background-position: 0 2.54em;
    background-repeat: repeat-x;
    background-size: 4px 1px;
    font-size: 14px;
    letter-spacing: 1px;
    line-height: 18px;
    padding: 10px 0;

    &:hover {
      background-image: linear-gradient(to right, $white 100%, $white 100%);
    }
  }

  .legal-link {
    width: 100%;
    text-align: center;
    font-weight: 500;
  }

  .footer-logo {
    max-width: 120px;
    margin-bottom: 7px;
  }

  #copyright {
    text-align: center;
    width: 100%;
    font-weight: 500;
    font-size: 14px;
    font-size: 14px;
    letter-spacing: 1px;
    line-height: 18px;
    padding: 10px 0;
  }
}

@media (max-width: $MQMobile) {
  .can-hide {
    display: none;
  }
}
</style>
