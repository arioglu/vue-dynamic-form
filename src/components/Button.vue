<template>
  <button class="wrapper" @click="operate">{{ label }}</button>
</template>

<script>
export default {
  name: "Button",
  components: {},
  props: {
    label: {
      type: String,
      default: "",
    },
  },
  data() {
    return {};
  },
  methods: {
    operate() {
      this.$emit(this.label.toLowerCase());
    },
  },
};
</script>

<style scoped lang="scss">
.wrapper {
  height: 40px;
  transition: background-color 0.5s ease;
  min-width: 100px;
  border: solid 0.1em;
  border-radius: 4px;
  padding: 7px 10px;
  background-color: #d5dee0;
  color: #576975;
  font-weight: 300;
  align-items: flex-end;
  justify-content: center;
  font-family: "Lato", sans-serif;
  margin: 0 5px;
  &:hover {
    background-color: #b68d92;
    color: #fff;
    cursor: pointer;
  }
  @media (max-width: 720px) {
    width: 50%;
  }
}
</style>