<template>
  <v-app>
    <header>
      <!-- importo valore $emit (@SearchApp); salvo valore in data con funzione setSearchContent-->
      <HeaderWeb @SearchApp="setSearchContent" />
    </header>
    <main>
      <!-- mando valore salvato in data (Content) a MainWeb come props -->
      <MainWeb :searchContent="searchTitle" />
    </main>
  </v-app>
</template>

<script>
import HeaderWeb from "./components/HeaderWeb";
import MainWeb from "./components/MainWeb";

export default {
  name: "App",
  data: () => ({
    searchTitle: "",
  }),
  methods: {
    setSearchContent(argomento) {
      this.searchTitle = argomento;
    },
  },
  components: {
    HeaderWeb,
    MainWeb,
  },
};
</script>
<style lang="scss" scoped>
main {
  padding-top: 3rem;
}
</style>
