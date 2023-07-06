<!-- 請使用官方的元件試玩工具：Vue SFC Playground

https://sfc.vuejs.org/

    請建立 MyInput.vue 元件，並支援下列功能
    v-model 能夠設定值、取得值
    label 能夠設定欄位名稱（可以不用像 Quasar 動畫那樣華麗，就簡單顯示在旁邊即可）
    filled 樣式
    outlined 樣式 -->

<script>
export default {
  props: {
    label: String,
    filled: Boolean,
    outlined: Boolean,
    modelValue: { type: String, defaultValue: null },
  },
  emits: ["update:modelValue"],
};
</script>

<template>
  <div class="container">
    <input
      id="input"
      :class="{ filled: filled, outlined: outlined }"
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      required
    />
    <label for="input">{{ label }}</label>
  </div>
</template>

<style>
.container {
  position: relative;
  margin: 50px;
}

label {
  position: absolute;
  left: 10px;
  top: 10px;
  transition: all 200ms linear;
  color: rgb(183, 179, 179);
}

input {
  width: 200px;
  padding: 20px 10px;
  transition: all 200ms linear;
}

input:focus ~ label,
input:valid ~ label {
  top: 0px;
  color: rgb(85, 212, 255);
  scale: 0.9;
}

.filled {
  color: rgb(183, 179, 179);
  background: rgb(67, 66, 66);
  border: none;
  border-bottom: 2px solid rgb(67, 66, 66);
  outline: none;
}
.filled:hover,
.filled:focus {
  border-bottom: 2px solid white;
  filter: brightness(1.1);
}

.outlined {
  color: rgb(183, 179, 179);
  background: rgb(48, 46, 46);
  border: 1px solid rgb(183, 179, 179);
  outline: none;
}
.outlined:hover,
.outlined:focus {
  border: 1px solid rgb(85, 212, 255);
  outline: 1px solid rgb(85, 212, 255);
  filter: brightness(1.1);
}
</style>
