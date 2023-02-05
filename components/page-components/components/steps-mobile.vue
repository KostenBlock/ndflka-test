<template>
  <div class="main">
    <div
      v-if="!isPressed"
      @click="() => isPressed = true"
      class="initial__container column"
    >
      <q-mark/>
      <p class="initial__text">Как мы работаем</p>
    </div>
    <div v-if="isPressed" class="steps__mobile row">
      <p class="header center-text">Как мы работаем</p>
      <div class="steps row">
        <div v-for="(step, index) in steps" :key="step.text" class="step row">
          <img :src="step.src" :alt="step.text">
          <p v-html="step.text" class="text center-text"/>
          <arrow-down v-if="index !== steps.length - 1" class="arrow__mobile"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ArrowDown from "~/static/images/arrow-down.svg?inline";
import QMark from "~/static/images/question-mark.svg?inline";

export default {
  name: "steps-mobile",
  components: { ArrowDown, QMark },
  props: {
    steps: {
      type: Array,
      default: []
    }
  },
  data: () => ({
    isPressed: false
  })
}
</script>

<style lang="scss" scoped>
@import "assets/css/variables";

.main {
  display: none;

  @media screen and (max-width: $tablet) {
    display: block;
  };
};

.initial__container {
  align-items: center;
  justify-content: center;
  gap: 7px;

  .initial__text {
    color: $violet;
    text-decoration: underline;
  };
};

.steps__mobile {
  gap: 25px;

  .steps {
    grid-auto-flow: row;
    gap: 5px;

    .step {
      justify-items: center;
      gap: 5px;

      .text {
        font-weight: 400;
        font-size: 16px;
        line-height: 20px;
      };
    };
  };
};

</style>
