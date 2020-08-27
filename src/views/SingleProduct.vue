<template>
  <div id="SingleProducts">
    <!-- Product View -->

    <!-- <v-row class="m-0 mt-4">
      <v-col class="bg-danger   " md="5" cols="12">
        <v-img
          :src="require(`../assets/5.jpg`)"
          class="ma-2 "
          width="300"
        ></v-img>

        <v-row class="d-flex flex-row">
          <v-col class="d-flex flex-row">
            <v-img
              :src="require(`../assets/5.jpg`)"
              width="50"
              class="ma-2"
            ></v-img>
            <v-img
              :src="require(`../assets/5.jpg`)"
              width="50"
              class="ma-2"
            ></v-img>
            <v-img
              :src="require(`../assets/5.jpg`)"
              width="50"
              class="ma-2"
            ></v-img>
            <v-img
              :src="require(`../assets/5.jpg`)"
              width="50"
              class="ma-2"
            ></v-img>
          </v-col>
        </v-row>
      </v-col>
      <v-col class="bg-info" md="7" cols="12">bb</v-col>
    </v-row> -->

    <v-row class="m-0">
      <!-- Product Image -->
      <v-col class="">
        <v-card elevation="24" max-width="444" class="mx-auto">
          <v-system-bar lights-out></v-system-bar>
          <v-list two-line>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title class="h1 text-center"
                  >Coleman 3 X 450ml Containers</v-list-item-title
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-list two-line>
            <v-list-item>
              <v-list-item-content>
                <v-img
                  :src="require('../assets/' + Product[0].images[tab].img)"
                ></v-img>
              </v-list-item-content>
            </v-list-item>
          </v-list>

          <!-- Mobile View -->
          <v-row class="m-0" v-if="this.$vssWidth <= 768">
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 0"
                v-if="Product[0].images[1]"
                style="cursor:pointer; width:2rem"
                :src="require('../assets/' + Product[0].images[0].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 1"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[1]"
                :src="require('../assets/' + Product[0].images[1].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 2"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[2]"
                :src="require('../assets/' + Product[0].images[2].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 3"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[3]"
                :src="require('../assets/' + Product[0].images[3].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 4"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[4]"
                :src="require('../assets/' + Product[0].images[4].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 5"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[5]"
                :src="require('../assets/' + Product[0].images[5].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 6"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[6]"
                :src="require('../assets/' + Product[0].images[6].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 7"
                style="cursor:pointer; width:2rem"
                v-if="Product[0].images[7]"
                :src="require('../assets/' + Product[0].images[7].img)"
              ></v-img>
            </v-col>
          </v-row>

          <!-- Desktop View -->
          <v-row class="m-0" v-else>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 0"
                v-if="Product[0].images[1]"
                style="cursor:pointer"
                :src="require('../assets/' + Product[0].images[0].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 1"
                style="cursor:pointer"
                v-if="Product[0].images[1]"
                :src="require('../assets/' + Product[0].images[1].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 2"
                style="cursor:pointer"
                v-if="Product[0].images[2]"
                :src="require('../assets/' + Product[0].images[2].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 3"
                style="cursor:pointer"
                v-if="Product[0].images[3]"
                :src="require('../assets/' + Product[0].images[3].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 4"
                style="cursor:pointer"
                v-if="Product[0].images[4]"
                :src="require('../assets/' + Product[0].images[4].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 5"
                style="cursor:pointer"
                v-if="Product[0].images[5]"
                :src="require('../assets/' + Product[0].images[5].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 6"
                style="cursor:pointer"
                v-if="Product[0].images[6]"
                :src="require('../assets/' + Product[0].images[6].img)"
              ></v-img>
            </v-col>
            <v-col md="3" sm="3">
              <v-img
                @click="tab = 7"
                style="cursor:pointer"
                v-if="Product[0].images[7]"
                :src="require('../assets/' + Product[0].images[7].img)"
              ></v-img>
            </v-col>
          </v-row>
        </v-card>
      </v-col>

      <!-- cart Info -->
      <v-col class="">
        <v-row>
          <v-col class="mt-5">
            <span class="h1 ">Coleman 3 X 450ml Containers</span>
          </v-col>
        </v-row>

        <v-row class="m-0">
          <v-col class="ma-0"
            >Factory directly: 100% food grade. Material: Stainless steel SS
            410. Size: 16-24CM. Soup & Stock Pots, stockpot set/ MIxing pot
            /cooking pot set, 1.With good quality of ss 410 . 2. lid: cover
            safety with steel lock solid. 3.body: an integrated and uniform
            density, anti-corrosion and durable, easy to clean. 4 .bottom: it
            adopts an aluminum package of pan steel structure, and uniform rapid
            heat conduction, so its heat accumulation effect is good.
            5.Besides,little lampblack, energy conservation and save time are
            its feature. 6.handle:strong and durable, rivet firmly locked all
            show Europe type style. 7.Surface treatment: high-grade optical lens
            processing, it is convenient to clean. Brand: My Home Number of
            pieces: 5 Durable Colourful and unique design Comes with lids for
            each pot Factory directly: 100% food grade Material: Stainless steel
            SS 410 Size: 16-24CM Soup & Stock Pots, stockpot set/ MIxing pot
            /cooking pot set Feature: Eco-Friendly
          </v-col>
        </v-row>
        <v-row>
          <v-col class="ma-3  " md="4">
            <span class="">Price: </span>
          </v-col>
          <v-col class="ma-3  " md="6">
            <span class=""> Rs. 179</span>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="ma-3" md="4" cols="12">
            <span class="">Measure Quantity</span>
          </v-col>
          <v-col class="ma-2" md="4" cols="12">
            <v-btn icon @click="quantity--">
              <v-icon color="light-blue darken-4">mdi-minus-circle</v-icon>
            </v-btn>

            <input
              type="text"
              v-model="quantity"
              min="4"
              max="10"
              class="p-2 border border-info w-50 "
            />

            <v-btn icon @click="quantity++">
              <v-icon color="light-blue darken-4"> mdi-plus-circle</v-icon>
            </v-btn>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="ma-3" cols="12" md="4">
            <span class="">Choose Volume</span>
            <!-- <v-spacer></v-spacer> -->
          </v-col>
          <v-col class=" ma-3" cols="12" md="4">
            <v-select
              :items="Product[0].volume"
              label="Select Volume"
              dense
              outlined
            ></v-select>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="ma-0" md="4" cols="12">
            <v-btn color="light-blue darken-4 ma-4" class="text-light">
              <v-icon>mdi-cart-outline</v-icon> ADD TO CART
            </v-btn>
          </v-col>
          <v-col class="ma-0" md="4" cols="12">
            <v-btn color="green accent-4 ma-4 " class="text-light">
              <v-icon>mdi-currency-usd-circle</v-icon> BUY NOW
            </v-btn>
          </v-col>
        </v-row>
      </v-col>
    </v-row>

    <!-- Footer Section -->
    <SocialSection />
    <SubsribeSection />
    <Footer />
  </div>
</template>

<script>
import SocialSection from "../components/SocialSection";
import SubsribeSection from "../components/SubsribeSection";
import Footer from "../components/Footer";

import VueScreenSize from "vue-screen-size";

export default {
  mixins: [VueScreenSize.VueScreenSizeMixin],
  name: "SingleProducts",
  components: {
    SocialSection,
    SubsribeSection,
    Footer,
  },
  data() {
    return {
      tab: 0,
      quantity: 1,
      Product: [
        {
          name: "Anchor 1K",
          image: "Anchor 1k-min.png",
          category: "Milk Powder",
          price: "Rs. 800",
          volume: [
            "1Kg",
            "1.5Kg",
            "2Kg",
            "2.5Kg",
            "3Kg",
            "3.5Kg",
            "4Kg",
            "4.5Kg",
            "5Kg",
          ],
          images: [
            {
              img: "1.png",
            },
            {
              img: "2.png",
            },
            {
              img: "3.jpg",
            },
            {
              img: "4.png",
            },
          ],
        },
      ],
      colors: ["green", "secondary"],
      cycle: false,
      slides: ["First", "Second", "Third", "Fourth", "Fifth"],
    };
  },
};
</script>

<style></style>
