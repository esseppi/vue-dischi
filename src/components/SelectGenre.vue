<template>
  <v-select :items="[genre]" label="Items"> </v-select>
</template>
<script>
export default {
  name: "SelectGenre",
  data: () => {
    return {
      selectData: null,
    };
  },

  props: { genre: String },
};
</script>