<script setup lang="ts">
import { ref, inject, watch, computed } from "vue";

const lang = computed(async () => await inject("lang"));

// const data = computed(async () => {
//   console.log("lang", lang.value);
//   return await import(`./JSON/${lang.value}.json`);
// });

console.log(await lang.value);
</script>
<template>
  <main>
    <article>
      <!-- <transition-group name="move" mode="out-in">
        <section v-for="section in data" :key="section.title">
          <h1>{{ section.title }}</h1>
          <p>{{ section.text }}</p>
        </section>
      </transition-group> -->
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
  transform: translateZ(100%);
}
.move-leave-active {
  position: fixed;
}

@media (max-width: 500px) {
  main {
    padding: 1rem;
  }
}
</style>
