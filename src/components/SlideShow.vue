<template>
  <v-carousel height="350" cycle hide-delimiter-background show-arrows-on-hover>
    <v-carousel-item v-for="(item, i) in items" :key="i" :src="item.src">
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          src:
            "https://i0.wp.com/www.ecommerce-nation.com/wp-content/uploads/2019/02/Shopping-cart-6-tips-to-design-it-and-take-your-checkouts-to-the-next-level.png?resize=1280%2C640&ssl=1",
        },
        {
          src:
            "https://acquire.io/wp-content/uploads/2017/04/8-Steps-to-Optimize-Your-Ecommerce-Shopping-Cart-Checkout-in-2020.png",
        },
        {
          src:
            "https://storage.googleapis.com/gweb-uniblog-publish-prod/original_images/Flagship_100_Blog_2880x1800_Apparel.jpg",
        },
        {
          src:
            "https://www.digitalcommerce360.com/wp-content/uploads/2019/03/shutterstock_1023018736.jpg",
        },
      ],
    };
  },
};
</script>
