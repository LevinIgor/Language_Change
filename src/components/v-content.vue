<script setup lang="ts">
import { computed } from "vue";
import textEng from "@/JSON/text-eng.json";
import textUa from "@/JSON/text-ua.json";

const props = defineProps(["lang"]);

const text = computed(() => {
  return contentLang.value;
});

const contentLang = computed(() => {
  return props.lang === "ENG" ? textEng : textUa;
});
</script>
<template>
  <main>
    <article>
      <transition-group name="move" mode="out-in">
        <section v-for="section in text" :key="section.title">
          <h1>{{ section.title }}</h1>
          <p>{{ section.text }}</p>
        </section>
      </transition-group>
    </article>
  </main>
</template>
<style scoped>
main {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  padding: 3rem;
}
article {
  max-width: 800px;
}
section {
  margin-bottom: 3rem;
}
h1 {
  font-size: 19px;
  font-weight: bold;
  margin-bottom: 5px;
}
.move-move, /* apply transition to moving elements */
.move-enter-active,
.move-leave-active {
  transition: all 0.5s cubic-bezier(0.455, 0.03, 0.515, 0.955);
}

.move-enter-from,
.move-leave-to {
  opacity: 0;
  transform: translateY(100%);
}
.move-leave-active {
  position: absolute;
}

@media (max-width: 500px) {
  main {
    padding: 1rem;
  }
}
</style>
