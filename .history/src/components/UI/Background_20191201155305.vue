<template>
  <div></div>
</template>
<script>
export default {
  name: "Background"
};
</script>

<style scoped>
div {
  background-image: url("./../../assets/bg.jpg");
  background-color: white;
  background-size: cover;
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  z-index: -1;
}
div:after {
  content: "";
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  background: rgba(246, 246, 246, 0.9);
}
</style>
