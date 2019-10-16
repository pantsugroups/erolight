<template>
  <mu-appbar style="width: 100%;background-color:hsla(0,0%,100%,.8);" >
    <mu-button icon slot="left" @click="menu.open = true">
      <mu-icon value="menu"></mu-icon>
    </mu-button>
      <a style="text-shadow:1px 1px 10px hsla(0,0%,100%,.3);">Ero Light</a>
    <mu-button flat slot="right">登录</mu-button>
  </mu-appbar>
</template>
<script>
export default {
  name: "NavBar",
  props: ["menu"],
  created(){
    
  },
};
</script>