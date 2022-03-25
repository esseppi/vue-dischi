
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
    <v-text-field
      label="Search"
      solo
      fill-height
      dense
      clearable
      @keyup.enter="$emit('SearchApp', SearchContent)"
      v-model="SearchContent"
    >
    </v-text-field>
    <v-btn @click="$emit('SearchApp', SearchContent)">Filtra</v-btn>
    <v-btn @click="$emit('SearchApp', '')">Elimina Filtro</v-btn>
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


