<script setup lang="ts">
import VHeader from "@/components/v-header.vue";
import VContent from "@/components/v-content.vue";
import { ref } from "vue";

const lang = ref("eng");
async function changeLang(_lang: any) {
  lang.value = _lang.value;
}
</script>

<template>
  <VHeader @change-lang="changeLang($event)" />
  <VContent :lang="lang" />
</template>

<style scoped></style>
