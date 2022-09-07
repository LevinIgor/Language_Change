<script setup lang="ts">
import VHeader from "@/components/v-header.vue";
import VContent from "@/components/v-content.vue";
import { ref, provide } from "vue";

const lang = ref("eng");

function changeLang(_lang: string) {
  lang.value = _lang;
  console.log("lang", lang.value);
}
provide("lang", lang);
</script>

<template>
  <VHeader @change-lang="changeLang($event.target.value)" :lang="lang" />
  <VContent />
</template>

<style scoped></style>
