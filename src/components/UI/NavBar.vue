<template>
  <mu-appbar style="width: 100%;" color="primary">
    <mu-button icon slot="left" @click="menu.open = true">
      <mu-icon value="menu"></mu-icon>
    </mu-button>
      Ero Light
    <mu-button flat slot="right">登录</mu-button>
  </mu-appbar>
</template>
<script>
export default {
  name: "NavBar",
  props: ["menu"]
};
</script>