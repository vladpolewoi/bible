<template>
  <div :class="['verse', isActive && 'active']">
    <div @click="onSelect" class="verse__main">
      <span class="verse__number">{{ index }}</span>
      <span class="verse__text">{{ verse.text }}</span>
    </div>
    <div v-if="isActive">
      <div class="line"></div>
      <span class="verse__eng">{{ verse.text_nasb }}</span>
      <div class="line"></div>
      <div class="verse__greek">
        <div
          v-for="item in verse.text_greek"
          :key="item.strong"
          class="verse__greek__item"
        >
          <div>{{ item.r }}</div>
          <div class="verse__greek__greek">{{ item.g }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  verse: {
    required: true,
    type: Object,
  },
  index: {
    required: true,
    type: Number,
  },
});
const test = props.index === 1 ? true : false;
const isActive = ref(test);

const onSelect = () => {
  isActive.value = !isActive.value;
};
</script>

<style lang="scss" scoped>
.verse {
  display: inline-block;
  transition: 0.1s;
  padding: 0 10px;

  &__main {
    display: inline;
  }

  &__number {
    display: inline-block;
    color: #7e8ce0;
    font-size: 10px;
    margin-right: 3px;
    font-weight: 600;
    transform: translateY(-7px);
  }

  &__text {
    display: inline;
    text-align: start;
    font-size: 18px;
    word-wrap: break-word;
    line-height: 2.5rem;
  }

  &__eng {
    font-size: 14px;
    line-height: 25px;
  }

  &__greek {
    display: flex;
    flex-wrap: wrap;
    &__item {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0 15px 15px 0;
    }

    &__greek {
      color: #5b6078;
    }
  }

  &.active {
    background-color: #373a49;
    border-radius: 5px;
    display: inline-block;
  }
}

.line {
  height: 1px;
  width: calc(100% + 20px);
  transform: translateX(-10px);
  background-color: #4a4e63;
  margin: 15px 0;
}
</style>
