<template>
  <v-container class="d-flex">
    <CardVue
      v-for="(card, index) in albums"
      :img="card.poster"
      :title="card.title"
      :key="index"
    />
  </v-container>
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
