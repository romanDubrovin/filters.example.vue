<template>
  <div class="news-item" :class="{ hide: section.isHide }">
    <h3>{{ section.title }}</h3>
    <div class="tags">
      <Tag
        v-for="(tag, i) in section.tags"
        :key="i"
        :tag="tag"
        :onClickTagInPost="onClickTagInPost"
      />
    </div>
  </div>
</template>

<script>
import Tag from "./Tag.vue";

export default {
  props: ["section", "onClickTagInPost"],
  components: {
    Tag
  }
};
</script>

<style scoped>
.hide {
  display: none;
}
</style>
