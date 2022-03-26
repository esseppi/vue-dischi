<template>
  <v-container>
    <v-select
      @change="searchGenr"
      label="Filtra un genere"
      v-model="searchGenre"
      :items="albums"
      item-text="genre"
      item-value="genre"
    >
    </v-select>
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
    albums: [],
    trying: null,
    searchGenre: "",
  }),
  props: {
    searchContent: String,
  },
  methods: {
    searchGenr() {
      console.log("computed searchGen eseguito");

      // for (let card = 0; card < this.albums.length; card++) {
      //   const element = this.albums[card];
      //   if (element.genre == this.searchGenre) {
      //     return this.albums.push(element);
      //   }
      // }
      return this.albums.filter((card) =>
        card.genre.toLowerCase().includes(this.searchGenre.toLowerCase())
      );
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
