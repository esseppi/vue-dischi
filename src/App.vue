<template>
  <v-app>
    <!-- importo valore $emit (@SearchApp); salvo valore in data con funzione setSearchContent-->
    <HeaderWeb @SearchApp="setSearchContent" />
    <!-- mando valore salvato in data (Content) a MainWeb come props -->
    <MainWeb :searchContent="Content" />
  </v-app>
</template>

<script>
import HeaderWeb from "./components/HeaderWeb";
import MainWeb from "./components/MainWeb";

export default {
  name: "App",
  data: () => ({
    Content: "",
  }),
  methods: {
    setSearchContent(argomento) {
      this.Content = argomento;
      console.log(argomento);
    },
  },

  components: {
    HeaderWeb,
    MainWeb,
  },
};
</script>
<style lang="scss" scoped>
</style>
