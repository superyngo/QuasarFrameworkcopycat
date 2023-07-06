<!-- 
請建立 MyBanner.vue 元件，並支援下列功能
預設的 slot 能夠放入公告內容
action slot 能夠在下一排最右側放入額外內容
rounded 樣式 -->
<script>
export default {
  props: {rounded: Boolean},
};
</script>

<template>
  <div class="container">
    <div :class="{rounded: rounded, banner: true}"><slot></slot></div>
    <div class="action"><slot name="action"></slot></div>
  </div>
</template>

<style>
.container {
  position: relative;
}
.banner {
  max-width: 100svw;
  font-size: 0.875rem;
  font-weight: 400;
  line-height: 1.25rem;
  letter-spacing: 0.01786em;
  font-family: Roboto, -apple-system, Avenir, BlinkMacSystemFont, Segoe UI,
    Helvetica, Arial, sans-serif;
  background-color: #7b1fa2;
  color: aliceblue;
  padding: 1rem 0.5rem 3rem;
}
.action {
  position: absolute;
  top: 3rem;
  right: 3rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.rounded {
  border-radius: 4px;
}
</style>
