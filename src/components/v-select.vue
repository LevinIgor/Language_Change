<script setup lang="ts">
import { ref, onMounted } from "vue";
import Language from "./icons/language.vue";

const emits = defineEmits(["change"]);
const langs = ref([] as any);
const isMenuShow = ref(false);

onMounted(async () => {
  langs.value = await import("@/JSON/languages.json");
});
</script>
<template>
  <div
    class="select"
    @mouseenter="isMenuShow = true"
    @mouseleave="isMenuShow = false"
  >
    <span></span>

    <Language class="icon" />

    <Transition name="fade">
      <section v-if="isMenuShow">
        <span
          @click="emits('change', lang), (isMenuShow = false)"
          class="select__item"
          v-for="lang in langs.default"
          :key="lang.id"
        >
          {{ lang.label }}
        </span>
      </section>
    </Transition>
  </div>
</template>
<style scoped>
.select {
  display: flex;
  align-items: center;
  height: var(--header-height);
}
.icon {
  height: 20px;
  width: 20px;
  cursor: pointer;
  transition: all 0.5s;
  margin-right: 20px;
}
section {
  position: absolute;
  top: 100%;
  max-width: min-content;
  z-index: 100;
  display: flex;
  flex-direction: column;
  border: 1px solid var(--border-color);
  transform-origin: top;
  user-select: none;
}
.select__item {
  box-sizing: border-box;
  width: 100%;
  background-color: var(--header-background-color);
  color: var(--text-color);
  padding: 10px 20px;
  cursor: pointer;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s cubic-bezier(0.23, 1, 0.32, 1);
}

.fade-enter-from,
.fade-leave-to {
  transform: scaleY(0);
}
</style>
