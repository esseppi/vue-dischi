<template>
  <v-container class="prova" fluid>
    <v-autocomplete
      class="width=50"
      @click:append="searchGenre = null"
      clear-icon="mdi-delete"
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
    albums: [],
    searchGenre: null,
  }),
  props: {
    searchContent: String,
  },
  methods: {},
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
<style lang="scss" scoped>
.prova {
  max-width: 1450px;
  margin: auto;
}
</style>