<template>
  <div class="panel">
    <TagButton
      v-for="(tag, index) in uniqueTags"
      :key="index"
      :onClickTagInPanel="onClickTagInPanel"
      :tag="tag"
    />
  </div>
</template>

<script>
import TagButton from "./TagButton.vue";

export default {
  props: ["onClickTagInPanel", "uniqueTags"],
  components: {
    TagButton
  }
};
</script>

<style scoped>
.panel {
  border: 1px solid black;
}
</style>
