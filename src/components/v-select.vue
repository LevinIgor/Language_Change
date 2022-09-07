<script setup lang="ts">
import { ref } from "vue";
import Language from "./icons/language.vue";
const data = ref([
  { value: "UA", text: "Українська" },
  { value: "ENG", text: "English" },
]);
</script>
<template>
  <div class="select">
    <div class="select__btn">
        
      <Language class="icon" />
    </div>
    <section>
      <span class="select__item" v-for="(item, index) in data" :key="index">
        {{ item.text }}
      </span>
    </section>
  </div>
</template>
<style scoped>
.select {
  display: flex;
  align-items: center;
}
.icon {
  height: var(--header-height);
  cursor: pointer;
  transition: all 0.5s;
  margin-right: 20px;
}
section {
  position: absolute;
  transform: translateY(50px);
  left: 0;
  max-width: min-content;
  z-index: 100;
  display: flex;
  flex-direction: column;
}
.select__item {
  box-sizing: border-box;
  width: 100%;
  background-color: var(--header-background-color);
  color: var(--text-color);
  padding: 10px 20px;
}
</style>
