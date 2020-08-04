<template>
  <div id="app">
    <h2>Panel with button</h2>
    <TagsPanel
      :uniqueTags="uniqueTags"
      :onClickTagInPanel="onClickTagInPanel"
    />
    <h2>Panel with News</h2>
    <NewsPanel :data="data" :onClickTagInPost="onClickTagInPost" />
  </div>
</template>

<script>
import NewsPanel from "@/components/NewsPanel.vue";
import TagsPanel from "@/components/TagsPanel.vue";

const data = [
  {
    title: "One",
    tags: ["#Инвестирование", "#Ипотека", "#Деньги"]
  },
  {
    title: "Two",
    tags: ["#Кредиты", "#Вклады", "#Банки"]
  },
  {
    title: "Three",
    tags: [
      "#Инвестирование",
      "#Кредиты",
      "#Ипотека",
      "#Вклады",
      "#Банки",
      "#Страхование",
      "#Деньги"
    ]
  }
];

const uniqueTags = [
  {
    name: "#Инвестирование",
    isChecked: false
  },
  {
    name: "#Кредиты",
    isChecked: false
  },
  {
    name: "#Ипотека",
    isChecked: false
  },
  {
    name: "#Вклады",
    isChecked: false
  },
  {
    name: "#Банки",
    isChecked: false
  },
  {
    name: "#Страхование",
    isChecked: false
  },
  {
    name: "#Деньги",
    isChecked: false
  }
];

export default {
  name: "App",
  components: {
    NewsPanel,
    TagsPanel
  },
  data() {
    return {
      data: data.map(section => ({
        ...section,
        tags: section.tags.map(tag => ({ name: tag, isChecked: false })),
        isHide: false
      })),
      uniqueTags: uniqueTags,
      filterIsOn: false
    };
  },
  methods: {
    onClickTagInPanel(tagInPanel) {
      tagInPanel.isChecked = !tagInPanel.isChecked;
      this.filterIsOn = false;
      if (tagInPanel.isChecked) {
        this.filterIsOn = true;
      }
      this.tagsClickWatcher(tagInPanel);
    },
    onClickTagInPost(tagInPost) {
      this.filterIsOn = false;
      this.uniqueTags.forEach(el => {
        if (el.name == tagInPost.name) {
          el.isChecked = !el.isChecked;
          if (el.isChecked) {
            this.filterIsOn = true;
          }
          return;
        }
      });
      this.tagsClickWatcher(tagInPost);
    },
    tagsClickWatcher(val) {
      this.data.forEach(section => {
        section.tags.forEach(tag => {
          if (val.name == tag.name) {
            tag.isChecked = !tag.isChecked;
          }
        });
      });
    }
  },

  watch: {
    filterIsOn: function() {
      console.log("chahged");
    }
  }
};
</script>

<style></style>
