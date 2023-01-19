<template>
  <div class="container">
    <ChapterView :chapter="chapter" />
  </div>
</template>

<script setup>
import { reactive } from "vue";
import ChapterView from "@/components/ChapterView.vue";
import data from "@/data.json";

const chapter = reactive(data.chapters[0]);
</script>

<style lang="scss">
@import "./styles/main.scss";

.container {
  padding: 0;
  margin: 0;
  width: 100%;
}
</style>
