<template>
  <div>
    <Navbar />
    <Nuxt />
    <Footer />
  </div>
</template>

<script>
import Navbar from "~/components/nvabar/navbar.vue";
import Footer from "~/components/footer/footer.vue";
export default {
  components: { Navbar, Footer },
  // async asyncData(context) {
  //   const { $content, app, params } = context;

  // },
};
</script>

<!--- Styling the page -->
<style scoped>

</style>
