<template>
  <v-app>
    <header>
      <HeaderWeb @SearchApp="setSearchContent" />
    </header>
    <v-main>
      <MainWeb />
    </v-main>
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
