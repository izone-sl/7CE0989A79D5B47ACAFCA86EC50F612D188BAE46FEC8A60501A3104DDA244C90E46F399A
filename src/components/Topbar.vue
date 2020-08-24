<template>
  <div id="Topbar">
    <!-- Desktop -->
    <div>
      <!-- Topbar -->
      <v-toolbar
        color="indigo darken-2"
        dark
        flat
        dense
        height="30"
        class="toolbar"
      >
        <v-spacer></v-spacer>
        <v-toolbar-items>
          <v-btn text x-small>
            <v-icon small>mdi-heart </v-icon> WishList
          </v-btn>
          <v-btn text x-small>
            <v-icon small>mdi-account</v-icon> Create an account
          </v-btn>
          <v-btn text x-small> <v-icon small>mdi-login</v-icon> Sign In </v-btn>
        </v-toolbar-items>
      </v-toolbar>

      <!--Responsive Toolbar -->
      <v-toolbar
        color="indigo darken-2"
        dark
        flat
        dense
        height="30"
        class="res_toolbar"
      >
        <v-toolbar-items>
          <v-btn text x-small>
            <v-icon small>mdi-heart </v-icon> WishList
          </v-btn>
          <v-btn text x-small>
            <v-icon small>mdi-account</v-icon> Create an account
          </v-btn>
          <v-btn text x-small> <v-icon small>mdi-login</v-icon> Sign In </v-btn>
        </v-toolbar-items>
      </v-toolbar>

      <!-- Main bar with Logo -->
      <v-app-bar
        color="light"
        hide-on-scroll
        extended=""
        dense
        light
        class="main_app_bar"
      >
        <v-toolbar-title class="mt-5 pt-5">
          <v-img src="../assets/web logo.png" width="90px"></v-img
        ></v-toolbar-title>
        <v-spacer></v-spacer>
        <v-col class="mt-14 ml-10" md="2" sm="12">
          <v-overflow-btn
            small
            :items="dropdown_font"
            label="ALL CATEGORIES"
            append-icon="mdi-chevron-down"
          ></v-overflow-btn>
        </v-col>

        <v-col class="searchContent " md="5" sm="12">
          <v-text-field
            outlined
            class="my-2"
            label="Search Products Here ... "
            dense
            append-outer-icon="mdi-shopping-search"
            @click:append-outer="underDevlopmentAlert"
          ></v-text-field>
        </v-col>
        <v-spacer></v-spacer>

        <div class="AppbarIcons">
          <v-btn
            class="ma-2 text-light mr-5"
            large
            fab
            color="indigo"
            @click="dialog = true"
          >
            <v-icon>mdi-cart</v-icon>
            <v-badge
              color="light-blue lighten-1"
              bordered
              offset-x="-10"
              offset-y="-5"
              content="6"
            ></v-badge>
          </v-btn>

          <span class="ml-4 mr-5 text-success">Rs. 10000</span>
        </div>
      </v-app-bar>

      <!--Responsive Main bar with Logo -->
      <v-app-bar
        color="light"
        hide-on-scroll
        extended=""
        dense
        light
        flat
        class="res_main_app_bar"
      >
        <v-app-bar-nav-icon
          class="mt-10"
          @click.stop="drawer = !drawer"
        ></v-app-bar-nav-icon>
        <v-spacer></v-spacer>
        <v-toolbar-title class="mt-5 pt-5">
          <v-img src="../assets/web logo.png" width="90px"></v-img
        ></v-toolbar-title>

        <v-spacer></v-spacer>

        <div class="AppbarIcons">
          <v-btn
            class="ma-3 text-light "
            small
            fab
            color="indigo"
            @click="dialog = true"
          >
            <v-icon>mdi-cart</v-icon>
            <v-badge
              color="light-blue lighten-1"
              bordered
              offset-x="-6"
              offset-y="-7"
              content="6"
            ></v-badge>
          </v-btn>
          <br />
          <span class="ml-0 mr-0  text-success">Rs. 10000</span>
        </div>
      </v-app-bar>

      <!-- Mobile Search and ALL Category -->
      <v-row class="Mobile_Search_and_CategoryMenu m-0">
        <v-col class="pa-3">
          <v-row>
            <v-col>
              <v-text-field
                outlined
                label="SEARCH THE STORE HERE"
                append-outer-icon="mdi-shopping-search"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row class="Mobile_Search_and_CategoryMenu m-0">
        <v-col>
          <v-toolbar flat>
            <v-toolbar dense flat color="indigo darken-3 text-light">
              <v-toolbar-title>ALL CATEGORIES</v-toolbar-title>

              <v-spacer></v-spacer>

              <v-icon
                class="text-light"
                @click="allCategory = false"
                v-if="allCategory"
                >mdi-menu</v-icon
              >
              <v-icon
                class="text-light"
                @click="allCategory = true" 
                v-if="!allCategory"
                >mdi-menu</v-icon
              >
            </v-toolbar>
          </v-toolbar>
        </v-col>
      </v-row>

      <v-row class="Mobile_Search_and_CategoryMenu m-0" v-if="allCategory">
        <v-col class="pa-3">
          <!-- ALL CATEGORIES -->
          <v-list dense>
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

                  <!-- Sub categories -->
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
          </v-list>
        </v-col>
      </v-row>

      <v-navigation-drawer app v-model="drawer" class="h-100" temporary>
        <!-- Drawer Header -->
        <v-list-item>
          <v-list-item-avatar>
            <v-img src="../assets/web logo.png"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title class="ma-2"> MENU </v-list-item-title>
          </v-list-item-content>
          <v-icon class="dark--text" right @click="drawer = !drawer"
            >mdi-close</v-icon
          >
        </v-list-item>

        <v-divider></v-divider>

        <!-- ALL CATEGORIES -->
        <v-list dense>
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
                  <!-- <v-list-tile-action>
                    
                  </v-list-tile-action> -->
                  <v-list-item-title>
                    <v-icon>{{ link.icon }}</v-icon
                    >{{ link.text }}</v-list-item-title
                  >
                </template>

                <!-- Sub categories -->
                <v-list
                  rounded
                  v-for="sublink in link.subLinks"
                  :to="sublink.to"
                  :key="sublink.text"
                >
                  <!-- <v-list-tile-action>
                    <v-icon>{{ sublink.icon }}</v-icon>
                  </v-list-tile-action> -->
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

          <!-- Sinlge Link -->
          <v-list-item v-for="item in items" :key="item.title" link>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

      <!-- Appbar on Scroll -->
      <v-app-bar
        fixed
        color="light-blue darken-4"
        inverted-scroll
        dark
        flat
        dense
        height="60"
        class="appbar_on_scroll"
      >
        <v-toolbar
          fixed
          color="light-blue darken-4"
          dark
          flat
          dense
          height="60"
        >
          <v-toolbar-items>
            <div class="ma-4">
              <span
                >ALL CATEGORIES
                <v-icon class="ml-8" @mouseover="drawer = !drawer"
                  >mdi-menu</v-icon
                ></span
              >
            </div>

            <v-btn text class="ml-12">
              <v-icon small>mdi-home</v-icon> HOME
            </v-btn>
            <v-btn text class="ml-2">
              <v-icon small>mdi-contacts</v-icon> CONTACT US
            </v-btn>
            <v-btn text class="ml-2">
              <v-icon small>mdi-progress-question</v-icon> FAQ
            </v-btn>
          </v-toolbar-items>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-text-field
              outlined
              class="my-2 searchbox"
              label="Search Products Here ... "
              dense
            ></v-text-field>
            <v-btn icon class="searchbtn">
              <v-icon>mdi-search-web</v-icon>
            </v-btn>
          </v-toolbar-items>

          <v-toolbar-items>
            <v-btn icon @click="dialog = true">
              <v-icon>mdi-cart</v-icon>
              <v-badge color="green" content="6"> </v-badge>
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-app-bar>

      <!--Responsive Appbar on Scroll -->
      <v-app-bar
        fixed
        color="light-blue darken-4"
        inverted-scroll
        dark
        flat
        dense
        height="60"
        class="res_appbar_on_scroll "
      >
        <v-toolbar color="light-blue darken-4" dark flat dense height="60">
          <v-toolbar-items>
            <v-btn icon @click.stop="drawer = !drawer">
              <v-icon small>mdi-menu</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon small>mdi-home</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon small>mdi-contacts</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon small>mdi-progress-question</v-icon>
            </v-btn>

            <v-menu :close-on-content-click="false" :nudge-width="200" offset-x>
              <template v-slot:activator="{ on, attrs }">
                <v-btn icon v-bind="attrs" v-on="on">
                  <v-icon>mdi-search-web</v-icon>
                </v-btn>
              </template>

              <v-card>
                <v-list>
                  <v-list-item>
                    <v-list-item-content>
                      <v-text-field
                        outlined
                        class="my-2 "
                        label="Search Products Here ... "
                        dense
                      ></v-text-field>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-menu>

            <v-btn icon @click="dialog = true">
              <v-icon>mdi-cart</v-icon>
              <v-badge color="green" content="6"> </v-badge>
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-app-bar>

      <!-- Cart Dialog -->
      <v-row justify="center">
        <v-dialog v-model="dialog" width="600px">
          <!-- <template v-slot:activator="{ on, attrs }">
            <v-btn color="primary" dark v-bind="attrs" v-on="on">
              Open Dialog
            </v-btn>
          </template> -->
          <v-card>
            <v-card-title>
              <span class="headline">Your Cart List</span>
            </v-card-title>
            <v-card-text
              >CART LIST FUNCTION HAS BEEN UNDER DEVELOPMENT
              PROCESS</v-card-text
            >
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="green darken-1" text @click="dialog = false"
                >Disagree</v-btn
              >
              <v-btn color="green darken-1" text @click="dialog = false"
                >Agree</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
    </div>
  </div>
</template>

<script>
import VueScreenSize from "vue-screen-size";

export default {
  mixins: [VueScreenSize.VueScreenSizeMixin],
  name: "Topbar",
  data: () => ({
    dropdown_font: [
      "All Grocery",
      "Fruits & Vegetables",
      "Meat & Fish",
      " Diary & Eggs",
      "Medicines",
      "Gas(Litro & Laugh)",
    ],
    drawer: null,
    allCategory: true,

    dialog: false,
    items: [
      { title: "Fruits & Vegetables", icon: "mdi-fruit-cherries" },
      { title: "Meat & Fish", icon: "mdi-fish" },
      { title: "Diary & Eggs", icon: "mdi-egg-easter" },
      { title: "Medicines", icon: "mdi-medical-bag" },
      { title: "Gas(Litro & Laugh)", icon: "mdi-gas-cylinder" },
      { title: "Water bottels", icon: "mdi-bottle-soda-classic" },
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
  }),
  methods: {
    underDevlopmentAlert() {
      alert("Under Development");
    },
  },
};
</script>

<style scoped>
::-webkit-scrollbar {
  display: none;
}
.searchContent {
  top: 30px;
}
.AppbarIcons {
  margin-top: 30px;
}
.searchbox {
  /* display: none; */
  opacity: 0.3;
}
.searchbox:hover {
  /* display: none; */
  opacity: 0.9;
}
.searchbtn:hover .searchbox {
  /* display: block;  */
  /* display: block; */
  opacity: 0.5;
  /* background-color: yellow; */
}

/* small size */
@media screen and (max-width: 320px) {
  .toolbar {
    display: none;
  }
  .appbar_on_scroll {
    display: none;
  }
  .main_app_bar {
    display: none;
  }
  .res_toolbar {
    display: block;
  }
  .res_main_app_bar {
    display: block;
  }
  .res_appbar_on_scroll {
    display: block;
  }
  .Mobile_Search_and_CategoryMenu {
    display: block;
  }
}

/* medium size */
@media screen and (max-width: 375px) {
  .toolbar {
    display: none;
  }
  .appbar_on_scroll {
    display: none;
  }
  .main_app_bar {
    display: none;
  }
  .res_toolbar {
    display: block;
  }
  .res_main_app_bar {
    display: block;
  }
  .Mobile_Search_and_CategoryMenu {
    display: block;
  }
}

/* large size */
@media screen and (max-width: 425px) {
  .toolbar {
    display: none;
  }
  .appbar_on_scroll {
    display: none;
  }
  .main_app_bar {
    display: none;
  }
  .res_toolbar {
    display: block;
  }
  .res_main_app_bar {
    display: block;
  }
  .Mobile_Search_and_CategoryMenu {
    display: block;
  }
}

/* tablet size */
@media screen and (max-width: 768px) {
  .toolbar {
    display: none;
  }
  .appbar_on_scroll {
    display: none;
  }
  .main_app_bar {
    display: none;
  }
  .res_toolbar {
    display: block;
  }
  .res_main_app_bar {
    display: block;
  }
  .Mobile_Search_and_CategoryMenu {
    display: block;
  }
}

/* laptop size */
@media screen and (min-width: 1024px) {
  .toolbar {
    display: block;
  }
  .appbar_on_scroll {
    display: block;
  }
  .main_app_bar {
    display: block;
  }
  .res_toolbar {
    display: none;
  }
  .res_main_app_bar {
    display: none;
  }
  .res_appbar_on_scroll {
    display: none;
  }
  .Mobile_Search_and_CategoryMenu {
    display: none;
  }
}
</style>
