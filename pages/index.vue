<template>
  <v-row>
    <v-col cols="8" class="" v-html="text"></v-col>
    <v-col cols="4"><v-img :src="img"/></v-col>
  </v-row>
</template>

<script>
export default {
  async mounted() {
    const { data } = await this.$axios.get(
      `https://demo-api.vsdev.space/api/farm/home_page`
    );
    this.text = data.text;
    this.img = data.image
  },
  data: () => ({
    text: "",
    img: "",
  }),
};
</script>