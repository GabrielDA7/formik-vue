<template>
  <div class="hello">
    <Formik :initialValues="{test:2, paas:2, check: true, textrsar: 'sssss', textrar: 'tsfd',tedt: 'testt', number: 21}" :onSubmit="handleSubmit">
      <Field name="test" class="formfield" component="select">
        <option class="test" id="qsd" value="1">test</option>
        <option value="2">test2</option>
      </Field>

      <Field name="check" component="checkbox" />

      <Field name="textrar" component="textarea" />

      <Field name="tedt" component="text" />

      <Field name="number" component="number" />

      <Field name="paas" component="password"/>

      <button type="submit">submit</button>
    </Formik>
  </div>
</template>

<script>
import Formik from "../formik/Formik.vue";
import Field from "../formik/Field.vue";

export default {
  name: "HelloWorld",
  components: {
    Formik,
    Field
  },
  methods: {
    handleSubmit: (e) => {window.console.log(e)}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
