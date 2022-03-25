<template>
  <v-app>
    <header>
      <HeaderWeb />
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

  components: {
    HeaderWeb,
    MainWeb,
  },

  data: () => ({
    //
  }),
};
</script>
<style lang="scss" scoped>
</style>
