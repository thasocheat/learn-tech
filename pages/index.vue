<template>
  <section class="px-4 py-12 mx-auto max-w-7xl">
   <h1>Welcome To Home Page</h1>
  </section>
</template>

<script>
export default {
  name: "IndexPage",
  head() {
    return {
      title: this.$config.SITE_TITLE + " | " + this.$t("home"),
      htmlAttrs: {
        lang: this.$i18n.locale,
      },
      meta: [
        {
          hid: "og:description",
          property: "og:description",
          content: "Learn Techonology",
        },
        {
          property: "og:title",
          hid: "og:title",
          content: this.$config.SITE_TITLE + " | " + this.$t("home"),
        },
        {
          hid: "og:image",
          property: "og:image",
          content: "/circle.png",
        },
      ],
    };
  },
  // mounted() {
  //   this.$auth.strategy.token.reset();
  //   this.$auth.strategy.refreshToken.reset();
  // },
};
</script>
