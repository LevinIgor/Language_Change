<script setup lang="ts">
import Change from "./icons/change.vue";
import Theme from "./icons/theme.vue";
import VSelect from "./v-select.vue";
import Language from "./icons/language.vue";
const emits = defineEmits(["changeLang"]);
const props = defineProps(["lang"]);

function nextLang() {
  props.lang === "ENG"
    ? emits("changeLang", { target: { value: "UA" } })
    : emits("changeLang", { target: { value: "ENG" } });
}
function changeTheme() {
  document.body.classList.toggle("dark");
}
</script>
<template>
  <header>
    <VSelect />
    <select :value="props.lang" @change="emits('changeLang', $event)">
      <option value="UA">Українська</option>
      <option value="ENG">English</option>
    </select>
    <Change class="icon rotate" @click="nextLang()" />
    <Theme class="icon" @click="changeTheme()" />
  </header>
</template>
<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: var(--header-height);
  background-color: var(--header-background-color);
  color: var(--text-color);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
  transition: color 0.6s ease, background-color 0.3s ease;
}
svg {
  fill: var(--text-color);
}
select {
  padding: 5px 10px;
}
.icon {
  width: 25px;
  height: 25px;
  cursor: pointer;
  margin-left: 20px;
  transition: all 0.5s;
}
.rotate:hover {
  transform: rotate(180deg);
}
</style>
