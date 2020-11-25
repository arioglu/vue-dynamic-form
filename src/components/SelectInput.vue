<template>
  <select
    :type="fieldObject.type"
    :name="fieldObject.name"
    :placeholder="fieldObject.label"
    v-model="model"
  >
    <option v-for="opt in fieldOpts" :key="`sel${opt}`">{{ opt }}</option>
  </select>
</template>

<script>
export default {
  name: "SelectInput",
  props: {
    fieldObject: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      selectedOption: "",
    };
  },
  computed: {
    model: {
      get() {
        return this.selectedOption;
      },
      set(value) {
        this.$emit("input", { name: this.fieldObject.name, value });
      },
    },
    fieldOpts() {
      return this.fieldObject.options;
    },
  },
};
</script>

<style scoped lang="scss">
</style>