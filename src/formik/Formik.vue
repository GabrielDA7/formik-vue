<template>
  <form class="formik-form" @submit.prevent="handleSubmit">
    <slot></slot>
  </form>
</template>

<script>
import { vueSet as set } from "vue-deepset";
export default {
  name: "Formik",
  props: {
    onSubmit: { type: Function, required: true },
    initialValues: { type: Object, required: true }
  },
  data() {
    return {
      values: JSON.parse(JSON.stringify(this.initialValues))
    };
  },
  provide() {
    return {
      formik: {
        values: this.values,
        change: this.handleChange
      }
    };
  },
  methods: {
    eventOrValue(e) {
      if (e instanceof Event) {
        if (e.target.options) {
          const selectedOption = e.target.options[e.target.selectedIndex];
          return selectedOption._value !== undefined
            ? selectedOption._value
            : selectedOption.value;
        }
        if (e.target.type === "checkbox") {
          return e.target.checked;
        }
        return e.target.value;
      }
      return e;
    },
    handleChange(e) {
      this.setValues({ [e.target.name]: this.eventOrValue(e) });
    },
    setValues(values) {
      Object.entries(values).forEach(([key, val]) => {
        set(this.values, key, val);
      });
    },
    handleSubmit() {
      this.onSubmit(this.values);
    }
  }
};
</script>
