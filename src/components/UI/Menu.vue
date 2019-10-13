<template>
  <mu-drawer :open.sync="menu.open" :docked="docked" :right="position === 'right'">
    <mu-list>
      <mu-list-item @click="menu.open = false" button>
        <mu-icon value="keyboard_arrow_left"></mu-icon>
      </mu-list-item>
      <mu-list-item button to="/">
        <mu-list-item-title>首页</mu-list-item-title>
      </mu-list-item>
      <mu-list-item button to="/query">
        <mu-list-item-title>分类</mu-list-item-title>
      </mu-list-item>
      <mu-list-item button>
        <mu-list-item-title>书架</mu-list-item-title>
      </mu-list-item>
    </mu-list>
  </mu-drawer>
</template>
<script>
export default {
  name: "Menu",
  data() {
    return {
      docked: false,
      position: "left"
    };
  },
  props: ["menu"]
};
</script>