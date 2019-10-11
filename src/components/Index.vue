<template>
  <div>
    <NavBar :menu="menu"></NavBar>
    <Menu :menu="menu"></Menu>
    <Background></Background>
    <mu-container style="margin-top:15px;">
      <mu-row>
        <mu-col span="12">
          <mu-paper class="demo-paper" :z-depth="3">
            <Carousel></Carousel>
          </mu-paper>
        </mu-col>
      </mu-row>
    </mu-container>
    <mu-container style="margin-top:15px;">
      <mu-row>
        <mu-col span="12">
          <mu-paper class="demo-paper" :z-depth="3">
            <mu-flex justify-content="center">
              <h2>首页推荐</h2>
            </mu-flex>
          </mu-paper>
        </mu-col>
      </mu-row>
    </mu-container>
    <mu-container>
      <mu-row gutter>
        <mu-col :key="1" span="12" sm="12" md="6" lg="4" xl="3" v-for="n in 12" style="margin-top:15px;">
          <mu-paper class="demo-paper" :z-depth="3">
            <mu-card>
              <mu-card-media title="幻兽调查员" sub-title="绫里惠史">
                <img src="@/assets/book1.jpg" />
              </mu-card-media>
              <mu-card-text>
                <mu-chip>
                  <mu-avatar :size="32">
                    <mu-icon value="date_range"></mu-icon>
                  </mu-avatar>2019-07-19 21:00:22
                </mu-chip>
                <mu-chip>
                  <mu-avatar :size="32">
                    <mu-icon value="local_offer"></mu-icon>
                  </mu-avatar>奇幻
                </mu-chip>
              </mu-card-text>
              <mu-card-actions>
                <mu-button color="secondary" full-width to="/archives/1">详情</mu-button>
              </mu-card-actions>
            </mu-card>
          </mu-paper>
        </mu-col>
      </mu-row>
    </mu-container>
  </div>
</template>

<script>
import Carousel from "@/components/UI/Carousel.vue";
import Background from "@/components/UI/Background.vue";
import NavBar from "@/components/UI/NavBar.vue";
import Menu from "@/components/UI/Menu.vue";
export default {
  name: "Index",
  data() {
    return {
      menu: {
        open: false
      }
    };
  },
  components: {
    NavBar,
    Menu,
    Carousel,
    Background
  }
};
</script>