<template>
  <v-list-item-title>
    <v-col>
      <v-row>Животные на нашей ферме</v-row>
      <v-row>Коров: {{ cows }}</v-row>
      <v-row>Кроликов: {{ rabbits }}</v-row>
      <v-row>Овец: {{ sheeps }}</v-row>
    </v-col>
    <v-img src="/img/left_widget_img.jpg"></v-img>
  </v-list-item-title>
</template>

<script>
export default {
  data() {
    return {
      cows: 0,
      rabbits: 0,
      sheeps: 0,
    };
  },
  async mounted() {
    const { data } = await this.$axios.get(
      `https://demo-api.vsdev.space/api/farm/left_widget`
    );
    this.cows = data.cows;
    this.rabbits = data.rabbits;
    this.sheeps = data.sheeps;
  },
};
</script>
