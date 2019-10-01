<template lang="pug">
  .indexpersonal-panel
    tabs.tabs-index(
      :tabs="tabs"
      :currentTab="currentTab"
      :wrapper-class="'default-tabs'"
      :tab-class="'default-tabs__item'"
      :tab-active-class="'default-tabs__item_active'"
      :line-class="'default-tabs__active-line'"
      @onClick="handleClick")
    .content
      div(v-if="currentTab === 'tab1'")
        <p>动态和消息放在一起是不是更好</p>
        <p>啦啦啦啦</p>
        <p>啦啦啦啦</p>
        <p>啦啦啦啦</p>
        <p>啦啦啦啦</p>
        <p>啦啦啦啦</p>
      div(v-if="currentTab === 'tab2'")
        <p>暂无消息</p>
      div(v-if="currentTab === 'tab3'")
        <p>你这个让我咋写嘛.jpg</p>
</template>
<script>
import Tabs from "vue-tabs-with-active-line";
export default {
  name: "Personal",
  components: { Tabs },
  data: () => ({
    tabs: [
      { title: " 动态", value: "tab1" },
      { title: " 消息", value: "tab2" },
      { title: " 个人", value: "tab3" }
    ],
    currentTab: "tab1"
  }),
  methods: {
    handleClick(newTab) {
      this.currentTab = newTab;
    }
  }
};
</script>