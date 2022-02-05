<template>
  <form @submit.prevent="submit">
    <v-col cols="12" v-for="(field, key) in form" :key="key">
      <v-text-field
        v-if="field.type === 'string'"
        v-model="formAns[key]"
        :label="field.title"
        required
      ></v-text-field>
      <v-select
        v-if="field.type === 'select'"
        v-model="formAns[key]"
        :items="field.values"
        :label="field.title"
        required
      ></v-select>
    </v-col>
    <button class="mr-4 btn" :class="{ error: error }">Отправить</button>
  </form>
</template>

<script>
export default {
  data: () => ({
    form: {},
    formAns: {},
    error: false,
  }),
  methods: {
    async submit() {
      if (
        this.formAns.type &&
        this.formAns.name &&
        this.formAns.color &&
        this.formAns.sex &&
        this.formAns.weight
      ) {
        this.formVis = false;
        await this.$axios.post(
          "https://demo-api.vsdev.space/api/farm/baby",
          this.formAns
        );
        this.formAns = {};
        this.$emit("serForm");
      } else {
          this.error = true
      }
    },
  },
  async mounted() {
    let { data } = await this.$axios.get(
      `https://demo-api.vsdev.space/api/farm/baby/form`
    );
    this.form = data.fields;
  },
  watch: {
    error(newValue) {
      setTimeout(() => {
        this.error = false;
      }, 500);
    },
  },
};
</script>

<style scoped>
.error{
    border: 1px solid red;
}
</style>