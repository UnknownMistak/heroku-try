<template>
  <v-card class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="200px"
      :src="`/img/${data.type}.jpg`"
    >
      <v-card-title>{{ data.name }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0"> Информация </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>Вес: {{ data.weight }}</div>
      <div>Цвет: {{ data.color }}</div>
      <div>Пол: {{ data.sex }}</div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
    },
  },
};
</script>
