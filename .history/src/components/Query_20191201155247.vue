<template>
  <div>
    <NavBar :menu="menu"></NavBar>
    <Menu :menu="menu"></Menu>
    <Background></Background>
    <mu-container style="margin-top:15px;">
      <mu-paper :z-depth="3">
        <mu-form
          :model="form"
          class="mu-demo-form"
          :label-position="labelPosition"
          label-width="100"
        >
          <mu-row>
            <mu-col span="8" offset="2" style="margin-top:30px;">
              <mu-form-item prop="input">
                <mu-text-field
                  v-model="form.input"
                  placeholder="输入关键字..."
                ></mu-text-field>
              </mu-form-item>
            </mu-col>
          </mu-row>
          <!-- <mu-row>
            <mu-col span="8" offset="2">
              <mu-form-item prop="radio" label="单选">
                <mu-radio v-model="form.radio" value="1" label="选项1"></mu-radio>
                <mu-radio v-model="form.radio" value="2" label="选项2"></mu-radio>
              </mu-form-item>
            </mu-col>
          </mu-row>
          <mu-row>
            <mu-col span="8" offset="2">
              <mu-form-item prop="checkbox" label="多选">
                <mu-checkbox v-model="form.checkbox" value="1" label="多选1"></mu-checkbox>
                <mu-checkbox v-model="form.checkbox" value="2" label="多选2"></mu-checkbox>
                <mu-checkbox v-model="form.checkbox" value="3" label="多选3"></mu-checkbox>
                <mu-checkbox v-model="form.checkbox" value="4" label="多选4"></mu-checkbox>
              </mu-form-item>
            </mu-col>
          </mu-row> -->
        </mu-form>
      </mu-paper>
    </mu-container>
    <mu-container>
      <mu-row gutter>
        <mu-col
          :key="n"
          span="12"
          sm="12"
          md="6"
          lg="4"
          xl="3"
          v-for="n in 12"
          style="margin-top:15px;"
        >
          <mu-paper class="demo-paper" :z-depth="3">
            <mu-card>
              <mu-card-media title="幻兽调查员" sub-title="绫里惠史">
                <img src="@/assets/book1.jpg" />
              </mu-card-media>
              <mu-card-text>
                <mu-chip>
                  <mu-avatar :size="32">
                    <mu-icon value="date_range"></mu-icon> </mu-avatar
                  >2019-07-19 21:00:22
                </mu-chip>
                <mu-chip>
                  <mu-avatar :size="32">
                    <mu-icon value="local_offer"></mu-icon> </mu-avatar
                  >奇幻
                </mu-chip>
              </mu-card-text>
              <mu-card-actions>
                <mu-button color="secondary" full-width to="/archives/1"
                  >详情</mu-button
                >
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
  name: "Query",
  data() {
    return {
      menu: {
        open: false
      },
      form: {
        input: "",
        select: "",
        date: "",
        radio: "",
        checkbox: [],
        switch: false,
        slider: 30,
        textarea: ""
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
