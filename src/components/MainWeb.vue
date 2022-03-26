<template>
  <v-container>
    <v-autocomplete
      @click:append="searchGenre = null"
      :append-icon="currentIcon[iconGenreIndex]"
      clearable
      label="Filtra un genere"
      v-model="searchGenre"
      :items="albums"
      item-text="genre"
      item-value="genre"
    >
    </v-autocomplete>
    <v-row class="justify-center">
      <CardVue
        v-for="card in searchCharacter"
        :img="card.poster"
        :title="card.title"
        :year="card.year"
        :genre="card.genre"
        :author="card.author"
        :searchGenr="searchGenre"
        :key="card.title"
      />
    </v-row>
  </v-container>
</template>

<script>
import CardVue from "./CardVuetify.vue";

export default {
  name: "MainWeb",
  components: { CardVue },
  data: () => ({
    iconGenreIndex: 1,
    currentIcon: ["mdi-delete", "mdi-select"],
    albums: [],
    searchGenre: null,
  }),
  props: {
    searchContent: String,
  },
  methods: {
    changeIconGenre() {
      // this.searchGenre == null
      //   ? this.iconGenreIndex == 0
      //   : this.iconGenreIndex == 1;
      if (this.searchGenre == null) {
        this.iconGenreIndex = 0;
      }
      console.log(this.iconGenreIndex);
    },
  },
  computed: {
    searchCharacter() {
      return this.albums.filter((card) =>
        card.title.toLowerCase().includes(this.searchContent.toLowerCase())
      );
    },
  },
  // PRENDO DATI DA API
  created() {
    const axios = require("axios");
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        // handle success
        this.albums = response.data.response;
        console.log(response.data.response);
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
    // .then(function () {
    //   // always executed
    // });
  },
};
</script>
