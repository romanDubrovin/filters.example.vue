<template>
  <div
    class="tag"
    @click="clickOnTagInPanel"
    :class="{ active: tag.isChecked }"
  >
    {{ tag.name }}
  </div>
</template>

<script>
export default {
  props: ["tag", "onClickTagInPanel"],
  methods: {
    clickOnTagInPanel() {
      this.onClickTagInPanel(this.tag);
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
