<!-- 請使用官方的元件試玩工具：Vue SFC Playground

https://sfc.vuejs.org/

    請建立 MyButton.vue 元件，並支援下列功能
    color 能夠設定背景顏色
    text-color 能夠設定文字顏色
    label 能夠設定文字內容
    size 能夠設定按鈕大小
    round 樣式
    square 樣式
    @click 能夠設定點擊後的任務 -->
<script>
export default {
  props: {
    color: String,
    textColor: String,
    label: String,
    size: Number,
    round: Boolean,
    square: Boolean,
  },
};
</script>

<template>
  <button
    class="myButton"
    @click="$emit('parentEvent', label)"
    :style="{
      background: color,
      color: textColor,
      borderRadius: Math.abs((round ? 50 : 0) - (square ? 5 : 0)) + 'px',
      lineHeight: `calc(${size} * 0.5rem)`,
      fontSize: `calc(${size}* 1rem)`,
      padding: `calc(${size} * 0.5rem)`,
      border: `calc(${size} * 0.05rem) solid black`,
    }"
  >
    {{ label }}
  </button>
</template>

<style>
.myButton {
  background: none;
  border: none;
  cursor: pointer;
}
.myButton:hover {
  scale: 1.1;
}
</style>
