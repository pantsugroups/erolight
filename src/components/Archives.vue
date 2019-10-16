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
                <img src="@/assets/book1.jpg" />
              </mu-card-media>
              <mu-card-actions>
                <mu-button color="primary" full-width to="/archives/1">立即阅读</mu-button>
                <mu-button color="secondary" full-width to="/archives/1">推送</mu-button>
                <mu-button color="success" full-width to="/archives/1">订阅</mu-button>
              </mu-card-actions>
            </mu-card>
          </mu-paper>
        </mu-col>
        <mu-col span="12" sm="12" md="6" lg="8" xl="9" style="hig">
          <mu-paper class="demo-paper" :z-depth="3" style="margin-top:15px;padding:15px 10px;">
            <mu-col>
              <h1 style="font-size:25px;">幻兽调查员</h1>
              <h3 style="font-size:12px;color:#969696;margin:0px 3px;">绫里惠史</h3>
              <p>小說講述了年紀輕輕便當上調查員的菲莉，與神秘幻獸克俢那以及『試管小人』的蝙蝠特洛一起，為了解決人與幻獸之間發生的各種問題，同時也為了完成世界唯一的幻獸書，在各地旅行的故事。</p>
              <span style="font-size:12px;color:#969696;margin:0px 3px;">奇幻</span>
            </mu-col>
          </mu-paper>
          <mu-paper class="demo-paper" :z-depth="3" style="margin-top:15px;">
            <mu-row gutter style="margin-top:15px;">
              <mu-col :key="n" span="4" sm="4" md="4" lg="3" xl="2" v-for="n in 3">
                <mu-card>
                  <mu-card-media sub-title="幻兽调查员[01]">
                    <img src="@/assets/book1.jpg" />
                  </mu-card-media>
                  <mu-card-actions>
                    <mu-button color="secondary" full-width to="/archives/1">详情</mu-button>
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
              <mu-form-item label="撰写评论">
                <mu-text-field v-model="value10" multi-line :rows="4" full-width></mu-text-field>
              </mu-form-item>
              <mu-form-item>
                <mu-button color="primary" round >提交评论</mu-button>
                <mu-button  round  color="grey500">取消回复</mu-button>
              </mu-form-item>
            </mu-form>
          </mu-paper>
          <mu-paper :z-depth="3" style="margin-top:15px">
            <mu-card>
              <mu-card-header title="bie" sub-title="2019-10-10 00:00">
                <mu-avatar slot="avatar" color="teal">
                  B
                  <!--<img src="ava.jpg" />!-->
                </mu-avatar>
              </mu-card-header>
              <mu-card-text style="padding:0px 30px;">
                <p>我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行我觉得不行</p>
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
          <mu-paper :z-depth="3" style="margin-top:15px">
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
  name: "Archives",
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