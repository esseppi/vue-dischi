<template>
  <main>
    <v-container>
      <v-row class="justify-center">
        <CardVue
          v-for="(card, index) in albums"
          :img="card.poster"
          :title="card.title"
          :year="card.year"
          :genre="card.genre"
          :author="card.author"
          :key="index"
        />
      </v-row>
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
