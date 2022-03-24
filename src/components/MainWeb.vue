<template>
  <CardVue />
</template>

<script>
import CardVue from "./CardVuetify.vue";
export default {
  name: "MainWeb",
  components: { CardVue },
  data: () => ({}),
  created() {
    const axios = require("axios");
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then(function (response) {
        // handle success
        console.log(response);
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
