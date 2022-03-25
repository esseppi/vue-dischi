<template>
  <main>
    <v-container @click="searchContent">
      <v-row class="justify-center">
        <CardVue
          v-for="(card, index) in searchCharacter"
          :img="card.poster"
          :title="card.title"
          :year="card.year"
          :genre="card.genre"
          :author="card.author"
          :key="index"
        />
      </v-row>
      <v-btn @click="searchCharacter">TRY</v-btn>
    </v-container>
  </main>
</template>

<script>
import CardVue from "./CardVuetify.vue";

export default {
  name: "MainWeb",
  components: { CardVue },
  data: () => ({
    albums: [],
  }),
  props: {
    searchContent: String,
  },
  methods: {
    try() {
      console.log(this.searchContent);
    },
  },
  computed: {
    searchCharacter() {
      console.log("computed searchCharacter eseguito");
      // eslint-disable-next-line max-len
      return this.albums.filter((card) =>
        card.title.toLowerCase().includes(this.searchContent.toLowerCase())
      );
    },
  },
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
