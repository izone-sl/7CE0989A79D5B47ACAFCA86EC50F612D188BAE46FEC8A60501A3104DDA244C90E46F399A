<template>
  <div id="Products">
    <!-- LATEST PRODUCTS -->
    <!-- Toolbar -->
    <v-row class="mt-3 m-0">
      <v-col>
        <v-toolbar height="40" flat>
          <v-toolbar-title>
            LATEST PRODUCTS
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn depressed color="cyan darken-3" class="text-light">
              View More
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-col>
    </v-row>
    <!-- Products -->
    <v-row class="m-0">
      <v-col class="mt-5">
        <v-sheet flat elevation="10">
          <v-slide-group class="pa-2" active-class="success">
            <v-slide-item
              v-for="(items, index) in Product"
              :key="index"
              v-slot:default="{ active, toggle }"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  flat
                  class="border py-2 m-2"
                  max-width="344"
                  style=" cursor: pointer;"
                
                >
                  <v-img
                    :src="require(`@/assets/` + items.image)"
                    height="200px"
                  >
                    <v-expand-transition>
                      <div
                        v-if="hover"
                        class="d-flex transition-fast-in-fast-out light-blue darken-4 v-card--reveal display-3 white--text"
                        style="height: 50%;"
                      >
                        {{ items.price }}
                      </div>
                    </v-expand-transition>
                  </v-img>
                  <v-card-title> {{ items.name }} </v-card-title>
                  <v-card-subtitle> {{ items.category }} </v-card-subtitle>
                  <v-card-subtitle> {{ items.price }} </v-card-subtitle>

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
                            to=""
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

                    <v-spacer></v-spacer>
                    <v-btn text disabled="">Share</v-btn>
                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-whatsapp</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on WhatsApp</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-facebook</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Facebook</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-instagram</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Instagram</span>
                      </v-tooltip>
                    </div>
                  </v-card-actions>
                </v-card>
              </v-hover>
            </v-slide-item>
          </v-slide-group>
        </v-sheet>
      </v-col>
    </v-row>

    <!-- HOT PRODUCTS -->
    <!-- Toolbar -->
    <v-row class="mt-3 m-0">
      <v-col>
        <v-toolbar height="40" flat>
          <v-toolbar-title>
            HOT PRODUCTS
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn depressed color="cyan darken-3" class="text-light">
              View More
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-col></v-row
    >
    <!-- Products -->
    <v-row class="m-0">
      <v-col class="mt-5">
        <v-sheet flat elevation="8">
          <v-slide-group class="pa-4" active-class="success">
            <v-slide-item
              v-for="(items, index) in Product.slice().reverse()"
              track-by="image"
              :key="index"
              v-slot:default="{ active, toggle }"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  flat
                  class="border py-2 ml-3"
                  max-width="344"
                  style=" cursor: pointer;"
                >
                  <v-img
                    :src="require(`@/assets/` + items.image)"
                    height="200px"
                  >
                    <v-expand-transition>
                      <div
                        v-if="hover"
                        class="d-flex transition-fast-in-fast-out light-blue darken-4 v-card--reveal display-3 white--text"
                        style="height: 50%;"
                      >
                        {{ items.price }}
                      </div>
                    </v-expand-transition>
                  </v-img>
                  <v-card-title> {{ items.name }} </v-card-title>
                  <v-card-subtitle> {{ items.category }} </v-card-subtitle>
                  <v-card-subtitle> {{ items.price }} </v-card-subtitle>

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
                            to=""
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

                    <v-spacer></v-spacer>
                    <v-btn text disabled="">Share</v-btn>
                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-whatsapp</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on WhatsApp</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-facebook</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Facebook</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-instagram</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Instagram</span>
                      </v-tooltip>
                    </div>
                  </v-card-actions>
                </v-card>
              </v-hover>
            </v-slide-item>
          </v-slide-group>
        </v-sheet>
      </v-col></v-row
    >

    <!-- LATEST PRODUCTS -->
    <!-- Toolbar -->
    <v-row class="mt-3 m-0">
      <v-col>
        <v-toolbar height="40" flat>
          <v-toolbar-title>
            LATEST PRODUCTS
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn depressed color="cyan darken-3" class="text-light">
              View More
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-col></v-row
    >
    <!-- Products -->
    <v-row class="m-0">
      <v-col class="mt-5">
        <v-sheet flat elevation="8">
          <v-slide-group class="pa-4" active-class="success">
            <v-slide-item
              v-for="(items, index) in Product"
              :key="index"
              v-slot:default="{ active, toggle }"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  flat
                  class="border py-2 ml-3"
                  max-width="344"
                  style=" cursor: pointer;"
                >
                  <v-img
                    :src="require(`@/assets/` + items.image)"
                    height="200px"
                  >
                    <v-expand-transition>
                      <div
                        v-if="hover"
                        class="d-flex transition-fast-in-fast-out light-blue darken-4 v-card--reveal display-3 white--text"
                        style="height: 50%;"
                      >
                        {{ items.price }}
                      </div>
                    </v-expand-transition>
                  </v-img>
                  <v-card-title> {{ items.name }} </v-card-title>
                  <v-card-subtitle> {{ items.category }} </v-card-subtitle>
                  <v-card-subtitle> {{ items.price }} </v-card-subtitle>

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
                            to=""
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

                    <v-spacer></v-spacer>
                    <v-btn text disabled="">Share</v-btn>
                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-whatsapp</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on WhatsApp</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-facebook</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Facebook</span>
                      </v-tooltip>
                    </div>

                    <div class="text-center">
                      <v-tooltip top>
                        <template v-slot:activator="{ on, attrs }">
                          <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-instagram</v-icon>
                          </v-btn>
                        </template>
                        <span>Share on Instagram</span>
                      </v-tooltip>
                    </div>
                  </v-card-actions>
                </v-card>
              </v-hover>
            </v-slide-item>
          </v-slide-group>
        </v-sheet>
      </v-col></v-row
    >
  </div>
</template>

<script>
import VueScreenSize from "vue-screen-size";

export default {
  mixins: [VueScreenSize.VueScreenSizeMixin],
  Name: "Products",
  data() {
    return {
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
</style>
