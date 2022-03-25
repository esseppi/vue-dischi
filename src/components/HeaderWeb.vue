
<template>
  <v-app-bar app>
    <div class="d-flex align-center">
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        src="../../public/img/logo.png"
        transition="scale-transition"
        width="40"
      />
    </div>

    <v-spacer></v-spacer>
    <v-text-field v-model="SearchContent"> </v-text-field>
    <v-btn @click="$emit('SearchApp', SearchContent)">spingi</v-btn>
    {{ SearchContent }}
  </v-app-bar>
</template>

<script>
export default {
  name: "HeaderWeb",
  data: () => {
    return {
      SearchContent: "",
    };
  },
};
</script>


