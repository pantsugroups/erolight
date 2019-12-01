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
        <mu-col
          :key="n.id"
          span="12"
          sm="12"
          md="6"
          lg="4"
          xl="3"
          v-for="n in novels"
          style="margin-top:15px;"
        >
          <mu-paper class="demo-paper" :z-depth="3">
            <mu-card>
              <mu-card-media v-bind:title="n.title" v-bind:sub-title="n.author">
                <img v-bind:src="n.cover" />
              </mu-card-media>
              <mu-card-text>
                <mu-chip>
                  <mu-avatar :size="32">
                    <mu-icon value="date_range"></mu-icon>
                  </mu-avatar>
                  {{n.update_time}}
                </mu-chip>
                <mu-chip v-for="t in n.tag" :key="t">
                  <mu-avatar :size="32">
                    <mu-icon value="local_offer"></mu-icon>
                  </mu-avatar>
                  {{t}}
                </mu-chip>
              </mu-card-text>
              <mu-card-actions>
                <mu-button color="secondary" full-width v-bind:to="'/archives/'+n.id">详情</mu-button>
              </mu-card-actions>
            </mu-card>
          </mu-paper>
        </mu-col>
      </mu-row>
    </mu-container>
    <mu-container style="margin-top:15px;margin-bottom:15px;">
      <mu-flex justify-content="center" v-on:click="flush()">
        <mu-pagination raised circle :total="pages" :current.sync="current" ref="pagination"></mu-pagination>
      </mu-flex>
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
  methods: {
    flush: function() {
      console.log(this.current);
      this.novels = [];
      fetch(
        this.$config.api_base + "novel/?page=" + this.current + "&page_size=16",
        {
          method: "get",
          credentials: "include"
        }
      )
        .then(data => data.json())
        .then(data => {
          if (data.status === 0 && data.count != 0) {
            data.data.forEach(element => {
              element.update_time = new Date(parseInt(element.update_at) * 1000)
                .toLocaleString()
                .replace(/:\d{1,2}$/, " ");
              element.tag = element.tags.split("/");
              this.novels.push(element);
            });
            this.pages = data.pages;
            window.pagination = this.$refs.pagination;
            console.log(data);
          }
        });
    }
  },
  created() {
    fetch(
      this.$config.api_base + "novel/?page=" + this.current + "&page_size=16",
      {
        method: "get",
        credentials: "include"
      }
    )
      .then(data => data.json())
      .then(data => {
        if (data.status === 0 && data.count != 0) {
          data.data.forEach(element => {
            element.update_time = new Date(parseInt(element.update_at) * 1000)
              .toLocaleString()
              .replace(/:\d{1,2}$/, " ");
            element.tag = element.tags.split("/");
            this.novels.push(element);
          });
          this.pages = data.pages;
          console.log(data);
        }
      });
  },
  data() {
    return {
      menu: {
        open: false
      },
      novels: [],
      current: 1,
      pages: 24
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
