<template>
  <input
    placeholder="Введите задачу ..."
    type="text"
    class="input"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
<script>
export default {
  name: "my-input",
  props: ["modelValue"],
  emits: ["update:modelValue"],
};
</script>
<style scoped>
.input {
  width: 70%;
  width: 70%;
  height: 45px;
  font-family: "Poppins", sans-serif;
  font-size: 15px;
  border: 2px solid #d1d3d4;
  padding: 12px;
  color: #111111;
  font-weight: 500;
  position: relative;
  border-radius: 5px;
}
.input:focus {
  outline: none;
  border-color: #8052ec;
}
</style>
