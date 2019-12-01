<template>
  <div>
    <NavBar :menu="menu"></NavBar>
    <Menu :menu="menu"></Menu>
    <Background></Background>
    <mu-container style="padding-bottom:30px;">
      <mu-row gutter style="margin-top:15px;">
        <mu-col span="12" sm="12" md="6" lg="4" xl="3">
          <mu-paper class="demo-paper" :z-depth="3" style="margin-top:15px;">
            <mu-card>
              <mu-card-media>
                <img v-bind:src="novel.cover" />
              </mu-card-media>
              <mu-card-actions>
                <mu-button color="primary" full-width to="/archives/1"
                  >立即阅读</mu-button
                >
                <mu-button color="secondary" full-width to="/archives/1"
                  >推送</mu-button
                >
                <mu-button color="success" full-width to="/archives/1"
                  >订阅</mu-button
                >
              </mu-card-actions>
            </mu-card>
          </mu-paper>
        </mu-col>
        <mu-col span="12" sm="12" md="6" lg="8" xl="9">
          <mu-paper
            class="demo-paper"
            :z-depth="3"
            style="margin-top:15px;padding:15px 10px;"
          >
            <mu-col>
              <h1 style="font-size:25px;">{{ novel.title }}</h1>
              <h3 style="font-size:12px;color:#969696;margin:0px 3px;">
                {{ novel.author }}
              </h3>
              <p>{{ novel.description }}</p>
              <span style="font-size:12px;color:#969696;margin:0px 3px;">{{
                novel.tags
              }}</span>
            </mu-col>
          </mu-paper>
          <mu-paper class="demo-paper" :z-depth="3" style="margin-top:15px;">
            <mu-row gutter style="margin-top:15px;">
              <mu-col
                :key="v.id"
                span="4"
                sm="4"
                md="4"
                lg="3"
                xl="2"
                v-for="v in volumes"
              >
                <mu-card>
                  <mu-card-media v-bind:sub-title="v.title">
                    <img v-bind:src="v.cover" />
                  </mu-card-media>
                  <mu-card-actions>
                    <mu-button color="secondary" full-width to="/archives/1"
                      >详情</mu-button
                    >
                  </mu-card-actions>
                </mu-card>
              </mu-col>
            </mu-row>
          </mu-paper>
          <mu-paper :key="1" :z-depth="3" style="margin-top:15px">
            <mu-flex class="flex-wrapper" justify-content="center">
              <mu-flex class="flex-demo" justify-content="center">
                <h3>书评区</h3>
              </mu-flex>
            </mu-flex>
          </mu-paper>
          <mu-paper :z-depth="3" style="margin-top:15px">
            <mu-form style="padding: 15px 15px 0px 15px">
              <mu-form-item v-bind:label="reply">
                <mu-text-field
                  v-model="comment"
                  multi-line
                  :rows="4"
                  full-width
                ></mu-text-field>
              </mu-form-item>
              <mu-form-item>
                <mu-button color="primary" round v-on:click="CreateComment"
                  >提交评论</mu-button
                >
                <mu-button round color="grey500">取消回复</mu-button>
              </mu-form-item>
            </mu-form>
          </mu-paper>
          <mu-paper
            :z-depth="3"
            style="margin-top:15px"
            v-for="c in comments"
            :key="c.id"
          >
            <mu-card>
              <mu-card-header
                v-bind:title="c.author_name"
                v-bind:sub-title="c.time"
              >
                <mu-avatar slot="avatar" color="red">
                  <img v-bind:src="c.author_avatar" />!
                </mu-avatar>
              </mu-card-header>
              <mu-card-text style="padding:0px 30px;">
                <mu-chip v-if="c.reply != 0">
                  <i>回复：“ {{ c.reply_title }}”</i>
                </mu-chip>
                <p>{{ c.title }}</p>
              </mu-card-text>
              <mu-card-actions>
                <mu-flex justify-content="end">
                  <mu-flex justify-content="center">
                    <mu-button small color="primary">回复</mu-button>
                  </mu-flex>
                </mu-flex>
              </mu-card-actions>
            </mu-card>
          </mu-paper>
          <!-- <mu-paper :z-depth="3" style="margin-top:15px">
            <mu-card>
              <mu-card-header title="ZF" sub-title="2019-10-10 00:01">
                <mu-avatar slot="avatar" color="red">
                  <img src="./../assets/avatar.jpg" />
                </mu-avatar>
              </mu-card-header>
              <mu-card-text style="padding:0px 30px;">
                <mu-chip>
                  <i>回复：“ 我觉得不行我觉得不行我觉得 ...... ”</i>
                </mu-chip>
                <p>我觉得你才不行</p>
              </mu-card-text>
              <mu-card-actions>
                <mu-flex justify-content="end">
                  <mu-flex justify-content="center">
                    <mu-button small color="primary">回复</mu-button>
                  </mu-flex>
                </mu-flex>
              </mu-card-actions>
            </mu-card>
          </mu-paper> -->
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
  name: "Archives",
  created() {
    fetch(this.$config.api_base + "novel/" + this.$route.params.id, {
      method: "get",
      credentials: "include"
    })
      .then(data => data.json())
      .then(data => {
        if (data.status === 0 && data.count != 0) {
          this.novel = data.data;
        }
      });
    fetch(this.$config.api_base + "novel/volume/" + this.$route.params.id, {
      method: "get",
      credentials: "include"
    })
      .then(data => data.json())
      .then(data => {
        if (data.status === 0 && data.count != 0) {
          data.data.forEach(element => {
            console.log(element);
            this.volumes.push(element);
          });
        }
      });
    fetch(
      this.$config.api_base + "comments/" + this.$route.params.id + "?type=2",
      {
        method: "get",
        credentials: "include"
      }
    )
      .then(data => data.json())
      .then(data => {
        if (data.status === 0 && data.count != 0) {
          data.data.forEach(element => {
            this.comments.push(element);
          });
        }
      });
  },
  data() {
    return {
      menu: {
        open: false
      },
      novel: {
        title: "",
        description: "",
        cover: "",
        author: "",
        tags: ""
      },
      volumes: [],
      comment: "",
      comments: [],
      reply: "撰写回复",
      reply_id: 0
    };
  },
  components: {
    NavBar,
    Menu,
    Carousel,
    Background
  },
  methods: {
    CreateComment() {}
  }
};
</script>
