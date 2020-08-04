<template>
  <div class="news">
    <NewsItem
      v-for="(section, index) in data"
      :key="index"
      :onClickTagInPost="onClickTagInPost"
      :section="section"
    />
  </div>
</template>

<script>
import NewsItem from "./NewsItem.vue";

export default {
  props: ["data", "onClickTagInPost"],
  components: {
    NewsItem
  }
};
</script>
