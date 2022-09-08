<script setup lang="ts">
import { ref, watch, onMounted } from "vue";

const props = defineProps(["lang"]);
const data = ref({ title: {}, body: { content: [{ title: "", text: "" }] } });

async function getData() {
  data.value = await import(`@/JSON/${props.lang}.json`);
}

watch(
  () => props.lang,
  () => getData()
);

onMounted(async () => {
  getData();
});
</script>
<template>
  <main>
    <article>
      <transition-group name="move" mode="out-in">
        <section v-for="section in data.body?.content" :key="section.title">
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
  margin-top: 50px;
}
article {
  max-width: 800px;
  user-select: none;
}
section {
  margin-bottom: 3rem;
}
h1 {
  font-weight: bold;
  margin-bottom: 5px;
  font-size: clamp(16px, 4vw, 24px);
}
p {
  font-size: clamp(12px, 2vw, 18px);
}
.move-move,
.move-enter-active,
.move-leave-active {
  transition: all 0.5s;
}

.move-enter-from,
.move-leave-to {
  opacity: 0;
  transform: translateY(50%);
}

@media (max-width: 500px) {
  main {
    padding: 1rem;
  }
}
</style>
