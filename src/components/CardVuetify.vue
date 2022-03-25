<template>
  <v-col cols="6" sm="4" md="3" lg="2">
    <v-card
      :loading="loading"
      class="
        mx-auto
        my-12
        flex flex-column
        justify-center
        text-center
        align-self-stretch
      "
      style="position: relative"
      width=""
      max-width="250"
    >
      <template slot="progress">
        <!-- Loading che si attiva nel caricamento button -->
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>
      <!-- Imagine Card -->
      <v-img height="250" :src="img"></v-img>
      <!-- Imagine Titolo -->
      <v-card-title class="justify-center">
        <h6>
          {{ title }}
        </h6>
      </v-card-title>

      <!-- Text Area -->
      <v-card-text>
        <!-- Autore -->
        <div class="my-2 text-subtitle-1">{{ author }}</div>
        <!-- Anno -->
        <div>{{ year }}</div>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>

      <v-card-actions class="d-flex justify-center">
        <v-btn color="deep-purple lighten-2" text @click="reserve">
          Acquista
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-col>
</template>
<script>
export default {
  name: "CardVuetify",
  data: () => ({
    loading: false,
    selection: 1,
  }),

  props: {
    img: String,
    title: String,
    author: String,
    genre: String,
    year: String,
  },

  methods: {
    reserve() {
      this.loading = true;
      setTimeout(() => (this.loading = false), 2000);
    },
  },

  // https://stackoverflow.com/questions/60908047/vuetify-v-card-fit-like-a-puzzle-masonry-layout
};
</script>
<style scoped lang="scss">
#colon {
  $colonne-md: 5;
  $colonne-sm: 3;
  $colonne-xs: 2;
  margin: 1rem;
  max-width: calc((100% / $colonne-md) - 2rem);
  flex-basis: 20%;
}
</style>