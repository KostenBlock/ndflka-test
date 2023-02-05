<template>
  <div class="main">
    <p class="header center-text">Как мы работаем</p>
    <div class="steps column">
      <div
        v-for="(step, index) in steps"
        :key="step.text"
        :class='`step row ${index % 2 !== 0 ? "step__down" : ""}`'
      >
        <div class="picture__container">
          <img :src="step.src" :alt="step.text" class="img">
          <arrow-down v-if="index !== steps.length - 1 && index % 2 === 0" class="arrow__down"/>
          <arrow-up v-if="index !== steps.length - 1 && index % 2 !== 0" class="arrow__up"/>
        </div>
        <div class="text__container">
          <div class="text__absolute">
            <p v-html="step.text" class="text center-text"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ArrowDown from "static/images/long-arrow-down.svg?inline";
import ArrowUp from "static/images/long-arrow-up.svg?inline";

export default {
  name: "steps-desktop",
  components: { ArrowDown, ArrowUp },
  props: {
    steps: {
      type: Array,
      default: []
    }
  },
}
</script>

<style lang="scss" scoped>
@import "assets/css/variables";

.main {
  display: grid;
  grid-auto-flow: row;
  gap: 25px;
  padding-bottom: 30px;

  @media screen and (max-width: $tablet) {
    display: none;
  };
};

.steps {
  justify-content: center;
  gap: 50px;

  .step {
    position: relative;
    align-self: start;
    justify-items: center;
    gap: 5px;
    max-width: 120px;

    .picture__container {
      position: relative;
      width: 121px;
      height: 120px;

      .img {
        z-index: 1;
      };

      .arrow__down {
        position: absolute;
        top: 100px;
        right: -75px;
      };

      .arrow__up {
        position: absolute;
        bottom: 117px;
        right: -55px;
      };
    };

    .text__container {
      position: relative;
      width: 100%;

      .text__absolute {
        position: absolute;
        left: 0;
        right: 0;
        display: flex;
        justify-content: center;

        .text {
          font-weight: 400;
          font-size: 16px;
          line-height: 20px;
          white-space: nowrap;
        };
      };
    };
  };

  .step__down {
    margin-top: 195px;
  };
};

</style>
