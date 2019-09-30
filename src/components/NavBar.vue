<template lang="pug">
.navbar
  .col-xs-12.col-sm-10.col-sm-offset-1.col-md-8.col-md-offset-2
    .nav
      .navbar-group
        .navbar-item.navbar-item-withicon.navbar-logo
          span.mdi.mdi-book-open-variant
          | Ero Light
        router-link.navbar-item(to="/") 首页
        router-link.navbar-item(to="/") 发现
      .navbar-group
        .navbar-item 登录
</template>
<script>
export default {
  name: "NavBar"
};
</script>