<template>
  <Form1 />
</template>
<script>
import Form1 from "./components/Form1.vue";
export default {
  components: {
    Form1,
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-content: center;
}
.form-control > * {
  display: block;
  margin-bottom: 12px;
}
span {
  display: block;
  color: red;
  margin-bottom: 1rem;
}
p {
  font-size: 20px;
  font-weight: bold;
  color: green;
}
</style>
