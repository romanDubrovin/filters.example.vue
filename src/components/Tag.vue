<template>
  <div @click="clickTagInPost" class="tag" :class="{ active: tag.isChecked }">
    {{ tag.name }}
  </div>
</template>

<script>
export default {
  props: ["tag", "onClickTagInPost"],
  methods: {
    clickTagInPost() {
      this.onClickTagInPost(this.tag);
    }
  }
};
</script>

<style scoped>
.tag {
  cursor: pointer;
  transition: 0.35s;
}
.tag.active {
  color: red;
}
</style>
