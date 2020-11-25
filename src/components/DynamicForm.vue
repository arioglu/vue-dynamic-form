
<template>
  <div>
    <form>
      <template v-for="field in formData">
        <label
          class="form-field"
          :for="field.name"
          :key="`label-${field.name}`"
          >{{ field.label }}</label
        >

        <template v-if="field.type === 'text'">
          <text-input
            class="input-field"
            :fieldObject="field"
            :key="`text_${field}`"
            @input="appendTextData"
            v-model="textModel"
        /></template>

        <template v-if="field.type === 'radio'">
          <radio-group
            :fieldObject="field"
            :key="`rd_${field}`"
            @input="appendRadioData"
            v-model="radioModel"
        /></template>

        <template v-if="field.type === 'select'">
          <select-input
            class="input-field"
            :fieldObject="field"
            :key="`select_${field.name}`"
            @input="appendSelectData"
            v-model="selectModel"
        /></template>

        <template v-if="field.type === 'textarea'">
          <text-area-input
            class="input-field__area"
            :fieldObject="field"
            :key="`select_${field}`"
            @input="appendTextAreaData"
            v-model="areaModel"
        /></template>
      </template>
    </form>
    <Button :label="'Submit'" @submit="showSubmitDate" />
  </div>
</template>

<script>
import RadioGroup from "./RadioGroup.vue";
import SelectInput from "./SelectInput.vue";
import TextInput from "./TextInput.vue";
import TextAreaInput from "./TextAreaInput.vue";
import Button from "./Button.vue";

export default {
  name: "FormComponent",
  components: { RadioGroup, SelectInput, TextInput, TextAreaInput, Button },
  data() {
    return {
      formData: [
        {
          label: "İsim, Soyisim",

          type: "text",

          name: "nameSurname",

          required: true,
        },
        {
          label: "Cinsiyet",

          type: "select",

          name: "gender",

          options: ["Erkek", "Kadın"],

          required: true,
        },
        {
          label: "Adres",

          type: "textarea",

          name: "address",

          required: false,
        },
        {
          label: "Mezuniyet Durumu",

          type: "radio",

          name: "graduationStatus",

          options: ["Mezun", "Öğrenci"],
        },
      ],
      formInfo: new Map(),
      radioModel: "",
      textModel: "",
      selectModel: "",
      areaModel: "",
    };
  },
  methods: {
    appendTextData(data) {
      this.formInfo.set(data.name, data.value);
    },
    appendTextAreaData(data) {
      this.formInfo.set(data.name, data.value);
    },
    appendSelectData(data) {
      this.formInfo.set(data.name, data.value);
    },
    appendRadioData(data) {
      this.formInfo.set(data.name, data.value);
    },
    showSubmitDate() {
      console.log("Data to be submitted");
      for (let [key, value] of this.formInfo) {
        console.log(key + " = " + value);
      }
    },
  },
};
</script>

<style scoped lang="scss">
.input-field {
  width: 150px;
  @media only screen and (max-width: 720px) {
    width: 50%;
  }
}
.input-field__area {
  width: 150px;
  height: 50px;
  @media only screen and (max-width: 720px) {
    width: 50%;
  }
}
.form-field {
  margin: 10px 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}
input {
  padding: 0;
}
textarea {
  padding: 0;
}
select {
  padding: 0;
}
</style>