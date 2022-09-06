<script setup lang="ts">
import VHeader from "@/components/v-header.vue";
import VContent from "@/components/v-content.vue";
import { ref } from "vue";

const lang = ref("ENG");

function changeLang(_lang: string) {
  lang.value = _lang;
}
</script>

<template>
  <VHeader @change-lang="changeLang($event.target.value)" :lang="lang" />
  <VContent :lang="lang" />
</template>

<style scoped></style>
