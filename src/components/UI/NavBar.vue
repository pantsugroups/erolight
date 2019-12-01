<template>
  <mu-appbar style="width: 100%;background-color:hsla(0,0%,100%,.8);">
    <mu-button icon slot="left" @click="menu.open = true">
      <mu-icon value="menu"></mu-icon>
    </mu-button>
    <a style="text-shadow:1px 1px 10px hsla(0,0%,100%,.3);">Ero Light</a>
    <mu-button flat slot="right" onclick="window.location.href='https://login.ero.ink'">{{ data.navbar }}</mu-button>
  </mu-appbar>
</template>
<script>
export default {
  name: "NavBar",
  props: ["menu"],
  data() {
    return {
      data: {
        navbar: "登陆"
      }
    };
  },
  created() {
    function getCookie(cname) {
      var name = cname + "=";
      var ca = document.cookie.split(";");
      for (var i = 0; i < ca.length; i++) {
        var c = ca[i].trim();
        if (c.indexOf(name) == 0) return c.substring(name.length, c.length);
      }
      return "";
    }
    let token = getCookie("token");

    if (token != "") {
      let userString = window.atob(token.split(".")[1]);

      let user = JSON.parse(userString).username;
      this.data.navbar = user;
    }
  }
};
</script>
