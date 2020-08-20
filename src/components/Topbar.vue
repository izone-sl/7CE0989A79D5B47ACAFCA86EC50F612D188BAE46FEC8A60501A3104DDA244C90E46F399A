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
          <v-btn class="ma-2 text-light mr-5" large fab color="indigo">
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
        class="res_main_app_bar"
      >
        <v-app-bar-nav-icon class="mt-10"></v-app-bar-nav-icon>
        <v-spacer></v-spacer>
        <v-toolbar-title class="mt-5 pt-5">
          <v-img src="../assets/web logo.png" width="90px"></v-img
        ></v-toolbar-title>

        <v-spacer></v-spacer>

        <div class="AppbarIcons">
          <v-btn class="ma-3 text-light " small fab color="indigo">
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
              <span>ALL CATEGORIES <v-icon class="ml-8">mdi-menu</v-icon></span>
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
            <v-btn icon>
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
        class="res_appbar_on_scroll"
      >
        <v-toolbar color="light-blue darken-4" dark flat dense height="60">
          <v-toolbar-items>
            <v-btn icon>
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

            <v-menu
              v-model="menu"
              :close-on-content-click="false"
              :nudge-width="200"
              offset-x
            >
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

            <v-btn icon>
              <v-icon>mdi-cart</v-icon>
              <v-badge color="green" content="6"> </v-badge>
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-app-bar>
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
  }),
  methods: {
    underDevlopmentAlert() {
      alert("Under Development");
    },
  },
};
</script>

<style scoped>
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
}
</style>
