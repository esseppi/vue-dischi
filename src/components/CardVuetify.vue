<template>
  <v-col>
    <v-card
      :loading="loading"
      class="mx-auto my-12 align-self-stretch"
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
      <v-card-title>{{ title }}</v-card-title>
      <!-- Text Area -->
      <v-card-text>
        <v-row align="center" class="mx-0">
          <!-- Autore -->
          <div class="my-2 text-subtitle-1">{{ author }}</div>
        </v-row>
        <!-- Anno -->
        <div>{{ year }}</div>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>

      <v-card-actions>
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
    justify: ["start", "end", "center", "baseline", "auto", "stretch"],
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
};
</script>
<style scoped lang="scss">
</style>