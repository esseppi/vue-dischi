
<template>
  <v-app-bar dense flat app>
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
    <v-btn @click="$emit('SearchApp', SearchContent)">
      <v-icon>mdi-magnify</v-icon>
    </v-btn>
    <v-text-field
      rounded
      single-line
      clearable
      class="shrink"
      hide-details="true"
      flat
      label="Cerca brano"
      dense
      @keyup.enter="
        $emit('SearchApp', SearchContent);
        cleanText();
      "
      v-model="SearchContent"
    >
    </v-text-field>
    <v-btn
      @click="
        $emit('SearchApp', '');
        cleanText();
      "
    >
      <v-icon>mdi-delete</v-icon>
    </v-btn>
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
  methods: {
    cleanText() {
      this.SearchContent = "";
    },
  },
};
</script>


