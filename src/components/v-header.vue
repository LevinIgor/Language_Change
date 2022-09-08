<script setup lang="ts">
import ThemeIcon from "./icons/theme.vue";
import VSelect from "./v-select.vue";
import { ref } from "vue";

const emits = defineEmits(["changeLang"]);
const header = ref({ language: "Change language", theme: "Theme" });

function changeTheme() {
  document.body.classList.toggle("dark");
}
async function changeLang(lang: any) {
  header.value = await import(`@/JSON/${lang.value}.json`).then(
    (res) => res.default.header
  );
  emits("changeLang", lang);
}
</script>
<template>
  <header>
    <section>
      <label>{{ header.language }}</label>
      <VSelect @change="changeLang($event)" />
    </section>
    <section>
      <label>{{ header.theme }}</label>
      <ThemeIcon class="icon" @click="changeTheme()" />
    </section>
  </header>
</template>
<style scoped>
header {
  box-sizing: border-box;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: var(--header-height);
  background-color: var(--header-background-color);
  color: var(--text-color);
  display: flex;
  justify-content: end;
  align-items: center;
  z-index: 100;
  transition: color 0.6s ease, background-color 0.3s ease;
  border-bottom: 1px solid var(--border-color);
}
section {
  display: flex;
  align-items: center;
  margin: 0 10px;
  font-size: clamp(10px, 2vw, 14px);
  padding: 5px;
}
section label {
  margin-right: 10px;
  color: var(--second-text-color);
  user-select: none;
}
svg {
  fill: var(--text-color);
}
select {
  padding: 5px 10px;
}
.icon {
  width: 20px;
  height: 20px;
  cursor: pointer;
  transition: all 0.5s;
}
.rotate:hover {
  transform: rotate(180deg);
}
</style>
