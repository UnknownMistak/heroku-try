<template>
  <v-row>
    <v-col cols="12">
      <v-btn @click="formVis = !formVis">Добавить живтное</v-btn>
    </v-col>
    <v-col cols="12" v-if="formVis">
      <myForm @serForm="upload" />
    </v-col>
    <v-col cols="6" v-for="animal in animals" :key="animal.id">
      <card :data="animal"></card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    formVis: false,
    animals: [],
  }),
  methods: {
    async upload() {
      const anim = await this.$axios.get(
        `https://demo-api.vsdev.space/api/farm/baby`
      );
      this.animals = anim.data;
      this.formVis = false
    },
  },
  async mounted() {
    const anim = await this.$axios.get(
      `https://demo-api.vsdev.space/api/farm/baby`
    );
    this.animals = anim.data;
  },
};
</script>
