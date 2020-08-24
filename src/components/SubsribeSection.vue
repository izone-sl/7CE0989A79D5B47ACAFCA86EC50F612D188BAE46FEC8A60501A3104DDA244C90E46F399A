r<template>
  <div id="SubsribeSection">
    <v-row class="m-0">
      <v-col class="sub">
        <v-row>
      
            <v-col class="root_subscribe">
              <div class="text-center ">
                <input
                  class="p-1 pl-4 border border-light w-75 text-light"
                  placeholder="ENTER YOUR EMAIL ADDRESS .."
                />
                <v-btn class="ma-3" tile color="indigo" dark>Subsribe</v-btn>
              </div>
            </v-col>
            <v-col class="ma-4 text-light root_subscribe">
              Sign up for new Customer, updates, surveys & offers
            </v-col>
   
          <!-- responsive -->

          <v-col class="res_subscribe">
            <div class="text-center ">
              <input
                class="p-1 pl-4 ma-1 border border-light w-100 text-light"
                placeholder="ENTER YOUR EMAIL ADDRESS .."
              />
              <v-btn class="ma-3" tile color="indigo" dark>Subsribe</v-btn>
              <br />
              <span class="text-light">
                Sign up for new Customer, updates, surveys & offers</span
              >
            </div>
          </v-col>
          <!-- <v-col class="ma-4 text-light">
           
          </v-col> -->
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "SubsribeSection",
  methods: {
    underDevlopmentAlert() {
      alert("Under Development");
    },
  },
};
</script>

<style scoped>
.sub {
  background-color: #311b90;
}
/* small size */
@media screen and (max-width: 320px) {
  .root_subscribe {
    display: none;
  }
  .res_subscribe {
    display: block;
  }
}

/* medium size */
@media screen and (max-width: 375px) {
  .root_subscribe {
    display: none;
  }
  .res_subscribe {
    display: block;
  }
}

/* large size */
@media screen and (max-width: 425px) {
  .root_subscribe {
    display: none;
  }
  .res_subscribe {
    display: block;
  }
}

/* tablet size */
@media screen and (max-width: 768px) {
  .root_subscribe {
    display: none;
  }
  .res_subscribe {
    display: block;
  }
}

/* laptop size */
@media screen and (min-width: 1024px) {
  .root_subscribe {
    display: block;
  }
  .res_subscribe {
    display: none;
  }
}
 
</style>
