<template>
  <v-app>
    <SlideShow />
    <!-- <v-container class=""> -->
    <div class="ma-5">
      <Products />
      <SocialSection />
    </div>
    <!-- </v-container> -->

    <SubsribeSection />
    <Footer />
  </v-app>
</template>

<script>
// @ is an alias to /src
import SlideShow from "../components/SlideShow";
import Products from "../components/Products";
import SocialSection from "../components/SocialSection";
import SubsribeSection from "../components/SubsribeSection";
import Footer from "../components/Footer";

export default {
  name: "Home",
  components: {
    SlideShow,
    Products,
    SocialSection,
    SubsribeSection,
    Footer,
  },
};
</script>
