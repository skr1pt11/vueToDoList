<template>
  <button class="button">
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: "my-button",
};
</script>
<style scoped>
.button {
  position: relative;
  float: right;
  width: 15%;
  height: 45px;
  border-radius: 6px;
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  font-size: 16px;
  background-color: #8052ec;
  border: none;
  color: #ffffff;
  cursor: pointer;
  outline: none;
}
</style>
