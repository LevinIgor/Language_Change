<script setup lang="ts">
import Change from "./icons/change.vue";
const emits = defineEmits(["changeLang"]);
const props = defineProps(["lang"]);

function nextLang() {
  props.lang === "ENG"
    ? emits("changeLang", { target: { value: "UA" } })
    : emits("changeLang", { target: { value: "ENG" } });
}
</script>
<template>
  <header>
    <select :value="props.lang" @change="emits('changeLang', $event)">
      <option value="UA">Українська</option>
      <option value="ENG">English</option>
    </select>
    <Change class="icon" @click="nextLang()" />
  </header>
</template>
<style scoped>
header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 50px;
  background-color: #000;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}
select {
  padding: 5px 10px;
}
.icon {
  width: 30px;
  height: 30px;
  cursor: pointer;
  margin-left: 20px;
  transition: all 0.5s;
}
.icon:hover {
  transform: rotate(180deg);
}
</style>
