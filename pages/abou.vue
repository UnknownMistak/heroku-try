<template>
  <v-row>
    <v-col cols="12" class="" v-html="text"></v-col>
  </v-row>
</template>

<script>
export default {
  async mounted() {
    const { data } = await this.$axios.get(
      `https://demo-api.vsdev.space/api/farm/about_page`
    );
    this.text = data.text;
  },
  data: () => ({
    text: "",
  }),
};
</script>
