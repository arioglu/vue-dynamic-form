<template >
  <div
    style="
      display: flex;
      align-items: flex-end;
      justify-content: center;
      margin: 10px 0;
    "
  >
    <div class="radio-group" v-for="opt in fieldOpts" :key="`rd-${opt}`">
      <label style="margin: 5px 0" for="one">{{ opt }}</label>
      <input
        type="radio"
        :name="fieldObject.name"
        :placeholder="fieldObject.label"
        :value="opt"
        v-model="model"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "RadioGroup",
  props: {
    fieldObject: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      radioSelect: {},
    };
  },
  computed: {
    model: {
      get() {
        return this.radioSelect;
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
.radio-group {
  display: flex;
  flex-direction: column;
}
label {
  width: 75px;
}
input {
  display: flex;
  width: 75px;
  justify-content: center;
  align-items: center;
}
</style>