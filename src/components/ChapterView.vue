<template>
  <div class="container">
    <VerseView
      v-for="(verse, index) in chapter.verses"
      :key="verse.id"
      :verse="verse"
      :index="index + 1"
    />
  </div>
</template>

<script setup>
import VerseView from "@/components/VerseView.vue";

defineProps({
  chapter: {
    required: true,
    type: Object,
  },
});
</script>

<style lang="scss" scoped>
.container {
  padding: 15px;
}
</style>
