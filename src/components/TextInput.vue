<template>
  <input
    :type="fieldObject.type"
    :name="fieldObject.name"
    :placeholder="fieldObject.label"
    v-model="model"
  />
</template>

<script>
export default {
  name: "TextInput",
  props: {
    fieldObject: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      inputString: "",
    };
  },
  computed: {
    model: {
      get() {
        return this.inputString;
      },
      set(value) {
        this.$emit("input", { name: this.fieldObject.name, value });
      },
    },
  },
};
</script>

<style scoped lang="scss">
</style>