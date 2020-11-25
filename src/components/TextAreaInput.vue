<template>
  <textarea
    :name="fieldObject.name"
    :placeholder="fieldObject.label"
    :id="fieldObject.name"
    v-model="model"
  >
  </textarea>
</template>

<script>
export default {
  name: "TextAreaInput",
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