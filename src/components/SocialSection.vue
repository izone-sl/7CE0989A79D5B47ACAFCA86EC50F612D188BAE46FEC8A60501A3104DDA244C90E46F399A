<template>
  <div id="SocialSection">
    Section
    <v-row>
      <v-col>
        <v-card  hover="" outlined rounded="">
          <v-card-title>Facebook</v-card-title>
          <v-card-text
            >Follow us on facebook You would have to be half mad to dream me
            up</v-card-text
          >
          <v-card-text>
            <v-btn class="ma-2" tile outlined color="primary">
              <v-icon left>mdi-facebook</v-icon> LIKE US
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card hover="" outlined rounded="">
          <v-card-title>Twitter</v-card-title>
          <v-card-text
            >Follow us on Twitter You would have to be half mad to dream me
            up.</v-card-text
          >
          <v-card-text>
            <v-btn class="ma-2" tile outlined color="primary">
              <v-icon left>mdi-twitter</v-icon> TWITTER NOW
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card hover="" outlined rounded="">
          <v-card-title>Instagram</v-card-title>
          <v-card-text
            >Follow us on instagram You would have to be half mad to dream me
            up.</v-card-text
          >
          <v-card-text>
            <v-btn class="ma-2" tile outlined color="primary">
              <v-icon left>mdi-instagram</v-icon> FOLLOW US
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "SocialSection",
};
</script>

<style></style>
