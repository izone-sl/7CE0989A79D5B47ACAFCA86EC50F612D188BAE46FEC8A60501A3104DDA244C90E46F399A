<template>
  <div class="products">
    <v-toolbar color="indigo darken-3" flat>
      <v-toolbar-items>
        <v-btn text>
          <v-icon class="text-light " left>mdi-grid</v-icon>
          <span class="text-light">PRODUCTS</span>
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>

    <v-row class="m-0 ">
      <!-- Filter Section -->
      <v-col class="pa-3 filter_section" md="3" cols="12">
        <!-- FILTER  -->
        <v-toolbar dense flat color="indigo darken-3 text-light">
          <v-toolbar-title>FILTER</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-list-group class="border">
          <template v-slot:activator>
            <v-list-item-title>Categories</v-list-item-title>
          </template>

          <v-list class="vlistScroll">
            <div v-for="(link, i) in links" :key="i">
              <v-list-tile
                v-if="!link.subLinks"
                :key="i"
                :to="link.to"
                :active-class="color"
                avatar
                class="v-list-item"
              >
                <v-list-tile-title v-text="link.text" />
              </v-list-tile>

              <v-list-group v-else :key="link.text" no-action>
                <template v-slot:activator>
                  <v-list-item-title>
                    <v-icon>{{ link.icon }}</v-icon
                    >{{ link.text }}</v-list-item-title
                  >
                </template>

                <v-list
                  rounded
                  v-for="sublink in link.subLinks"
                  :to="sublink.to"
                  :key="sublink.text"
                >
                  <v-list-item-group color="primary">
                    <v-list-item>
                      <v-list-item-content>
                        <v-list-item-title
                          v-text="sublink.text"
                        ></v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-item-group>
                </v-list>
              </v-list-group>
            </div>
          </v-list>
        </v-list-group>

        <v-list-group class="border">
          <template v-slot:activator>
            <v-list-item-title>Price</v-list-item-title>
          </template>
          <v-list class="vlistScroll">
            <v-list-item>
              <v-list-item-content>
                <v-range-slider
                  v-model="range"
                  :max="max"
                  :min="min"
                  class="align-center flex-column"
                  dense
                >
                  <template v-slot:prepend>
                    <div class="ma-4">Rs - {{ range[0] }}</div>
                    <div class="ma-4">Rs - {{ range[1] }}</div>
                  </template>
                  <template v-slot:append>
                    <v-btn class="ma-2" tile color="indigo" dark>
                      GO
                    </v-btn>
                  </template>
                </v-range-slider>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-list-group>

        <!-- Wish List -->
        <v-toolbar dense flat color="indigo darken-3 text-light mt-5">
          <v-toolbar-title>MY WISH LIST</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-list class="border">
          <v-list-item>
            <span class="lead">You have no items in your wish list.</span>
          </v-list-item>
        </v-list>
      </v-col>

      <!-- Products  Section -->
      <v-col class="">
        <v-toolbar class="filter_section" height="48px" dense>
          <v-toolbar-title>
            <v-btn icon>
              <v-icon small="">mdi-grid</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon small="">mdi-format-list-text</v-icon>
            </v-btn>
          </v-toolbar-title>

          <v-spacer></v-spacer>

          <v-toolbar-title>
            <v-col class="d-flex" cols="12" sm="12">
              <v-select
                :items="items"
                label="Sort By"
                dense
                class="mt-5"
                outlined
              ></v-select>
            </v-col>
          </v-toolbar-title>
        </v-toolbar>

        <!-- Responsive Filter -->
        <v-toolbar class="res_filter_section" dense height="48px">
          <v-btn text>
            <v-icon x-small="" color="blue">mdi-filter</v-icon> Filter
          </v-btn>
          <v-spacer></v-spacer>

          <v-select
            :items="items"
            label="Sort By"
            dense
            class="mt-5 ml-5"
            outlined
          ></v-select>
        </v-toolbar>

        <!-- PRODUCTS LIST -->
        <v-container>
          <v-row justify="space-around">
            <v-col v-for="(item, i) in Product" :key="i" cols="12" md="3">
              <v-sheet class="pa-2" color="grey lighten-3">
                <v-hover v-slot:default="{ hover }">
                  <v-card
                    flat
                    class=" py-2  "
                    max-width="300"
                    style=" cursor: pointer;"
                  >
                    <v-img
                      :src="require(`@/assets/` + item.image)"
                      height="200px"
                    >
                      <v-expand-transition>
                        <div
                          v-if="hover"
                          class="d-flex transition-fast-in-fast-out light-blue darken-4 v-card--reveal display-3 white--text"
                          style="height: 50%;"
                        >
                          {{ item.price }}
                        </div>
                      </v-expand-transition>
                    </v-img>

                    <v-card-title> {{ item.name }} </v-card-title>
                    <v-card-subtitle>
                      {{ item.category }} <br />
                      {{ item.price }}</v-card-subtitle
                    >
                    <v-card-actions>
                      <div class="text-center">
                        <v-tooltip top>
                          <template v-slot:activator="{ on, attrs }">
                            <v-btn color="purple" text v-bind="attrs" v-on="on">
                              <v-icon>mdi-cart-outline</v-icon>
                            </v-btn>
                          </template>
                          <span>ADD TO CART</span>
                        </v-tooltip>
                      </div>

                      <div class="text-center">
                        <v-tooltip top>
                          <template v-slot:activator="{ on, attrs }">
                            <v-btn
                              color="purple"
                              to="/product" 
                              class="LinkDecorate"
                              text
                              v-bind="attrs"
                              v-on="on"
                            >
                              <v-icon>mdi-eye</v-icon>
                            </v-btn>
                          </template>
                          <span>View About Product</span>
                        </v-tooltip>
                      </div>
                    </v-card-actions>
                  </v-card>
                </v-hover>
              </v-sheet>
            </v-col>
          </v-row>
        </v-container>
      </v-col>

      <v-col class="pa-3 res_wishlist_section" md="3" cols="12">
        <!-- Wish List -->
        <v-toolbar dense flat color="indigo darken-3 text-light mt-5">
          <v-toolbar-title>MY WISH LIST</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-list class="border">
          <v-list-item>
            <span class="lead">You have no items in your wish list.</span>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>

    <SubsribeSection />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src

import SubsribeSection from "../components/SubsribeSection";
import Footer from "../components/Footer";

export default {
  name: "Home",
  components: {
    SubsribeSection,
    Footer,
  },
  data() {
    return {
      allCategory: false,
      min: 0,
      max: 10000,
      slider: 40,
      range: [0, 9999],
      items: ["Product Name", "Price"],
      elevations: [6, 12, 18],
      Product: [
        {
          name: "Anchor 1K",
          image: "Anchor 1k-min.png",
          category: "Milk Powder",
          price: "Rs. 800",
        },

        {
          name: "Marmite",
          image: "1.png",
          category: "Food",
          price: "Rs. 400",
        },
        {
          name: "Topping",
          image: "2.png",
          category: "Food",
          price: "Rs. 270",
        },
        {
          name: "MD Orange",
          image: "3.jpg",
          category: "Drinks",
          price: "Rs. 145",
        },
        {
          name: "Orange Drink",
          image: "4.png",
          category: "Food",
          price: "Rs. 94",
        },
        {
          name: "Seman",
          image: "5.jpg",
          category: "Toothpaste",
          price: "Rs. 75",
        },
        {
          name: "Sensodyn",
          image: "6.jpg",
          category: "Personal Care",
          price: "Rs. 85",
        },
        {
          name: "Fair & Lovely",
          image: "7.jpg",
          category: "Personal Care",
          price: "Rs. 135",
        },
        {
          name: "Close up",
          image: "8.jpg",
          category: "Personal Care",
          price: "Rs. 65",
        },
        {
          name: "baby cheramy",
          image: "9.jpg",
          category: "Baby Care",
          price: "Rs. 186",
        },
      ],
      links: [
        {
          to: "/dashboard",
          icon: "mdi-tools",
          text: "Home & Appliances",
          subLinks: [
            {
              text: "Kitchen appliance",
              to: "/players",
            },
            {
              text: "Kitchen ware",
              to: "/players",
            },
            {
              text: "Cooling & Heating",
              to: "/players",
            },
            {
              text: "Vacums & Floor care",
              to: "/players",
            },
            {
              text: "Irons",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-power-plug-outline",
          text: "Electronic Accessories",
          subLinks: [
            {
              text: "Mobile accessories",
              to: "/players",
            },
            {
              text: "Audio",
              to: "/players",
            },
            {
              text: "Wearable",
              to: "/players",
            },
            {
              text: "Computer & laptop accessories",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-account-heart",
          text: "Health & Beauty",
          subLinks: [
            {
              text: "Bath & Body",
              to: "/players",
            },
            {
              text: "Beauty tools",
              to: "/players",
            },
            {
              text: "Hair care",
              to: "/players",
            },
            {
              text: "Makeup",
              to: "/players",
            },
            {
              text: "Men's care",
              to: "/players",
            },
            {
              text: "Skin care",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-baby",
          text: "Babies & Toys",
          subLinks: [
            {
              text: "Baby gear",
              to: "/players",
            },
            {
              text: "Baby Personal care",
              to: "/players",
            },
            {
              text: "Baby safety",
              to: "/players",
            },
            {
              text: "Gifts",
              to: "/players",
            },
            {
              text: "Clothing & accessories",
              to: "/players",
            },
            {
              text: "Nursery",
              to: "/players",
            },
            {
              text: "Baby & toddler toys",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-human",
          text: "Men's Fashion",
          subLinks: [
            {
              text: "Men's bags",
              to: "/players",
            },
            {
              text: "Men's shoes",
              to: "/players",
            },
            {
              text: "Men's accessories",
              to: "/players",
            },
            {
              text: "Men's underware",
              to: "/players",
            },
            {
              text: "Boy's fashion",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-human-female",
          text: "Women's Fashion",
          subLinks: [
            {
              text: "Shoes",
              to: "/players",
            },
            {
              text: "Bags",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-watch",
          text: "Watches & Accessories",
          subLinks: [
            {
              text: "Men's Watches",
              to: "/players",
            },
            {
              text: "Women's Watches",
              to: "/players",
            },
            {
              text: "Kids Watches",
              to: "/players",
            },
            {
              text: "Sunglasses   ",
              to: "/players",
            },
          ],
        },
        {
          to: "/dashboard",
          icon: "mdi-run-fast",
          text: "Sports & Outdoors",
          subLinks: [
            {
              text: "Men's shoes & clothing",
              to: "/players",
            },
            {
              text: "Women's shoes & clothing",
              to: "/players",
            },
            {
              text: "Outdoor recreation",
              to: "/players",
            },
            {
              text: "Exercise & fitness",
              to: "/players",
            },
            {
              text: "water sorts",
              to: "/players",
            },
            {
              text: "boxing & martial arts",
              to: "/players",
            },
            {
              text: "tennis",
              to: "/players",
            },
            {
              text: "badminten",
              to: "/players",
            },
            {
              text: "table tennis",
              to: "/players",
            },
            {
              text: "football",
              to: "/players",
            },
            {
              text: "basketball",
              to: "/players",
            },
            {
              text: "cricket",
              to: "/players",
            },
            {
              text: "rugby",
              to: "/players",
            },
          ],
        },
        //   {
        //     to: "/dashboard",
        //     ,
        //     text: "",
        //     subLinks: {},
        //   },
      ],
    };
  },
};
</script>
<style lang="css" scoped>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
.LinkDecorate {
  text-decoration: none;
}
/* small size */
@media screen and (max-width: 320px) {
  .filter_section {
    display: none;
  }
  .res_filter_section {
    display: block;
  }
}

/* medium size */
@media screen and (max-width: 375px) {
  .filter_section {
    display: none;
  }
  .res_filter_section {
    display: block;
  }
}

/* large size */
@media screen and (max-width: 425px) {
  .filter_section {
    display: none;
  }
  .res_filter_section {
    display: block;
  }
}

/* tablet size */
@media screen and (max-width: 768px) {
  .filter_section {
    display: none;
  }
  .res_filter_section {
    display: block;
  }
}

/* laptop size */
@media screen and (min-width: 1024px) {
  .filter_section {
    display: block;
  }
  .res_filter_section {
    display: none;
  }
  .res_wishlist_section {
    display: none;
  }
}
</style>
