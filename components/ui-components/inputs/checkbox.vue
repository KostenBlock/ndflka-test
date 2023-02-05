<template>
  <div class="input__container column">
    <p v-if="label !== ''" v-html="label" class="label"/>
    <div
      @click="() => changeEvent()"
      class="checkbox"
      :style="{border: isChecked ? 'none' : ''}"
    >
      <check  v-if="isChecked" />
    </div>
  </div>
</template>

<script>
export default {
  name: "checkbox",
  components: {
    check: () => import('~/static/images/check.svg?inline')
  },
  props: {
    label: {
      type: String,
      default: "",
    },
    isChecked: {
      type: Boolean,
      default: false,
    },
    changeEvent: {
      type: Function,
      default: () => {},
    },
  }
}
</script>

<style lang="scss" scoped>
@import "assets/css/variables";

.input__container {
  align-items: center;
  gap: 10px;

  .label {
    font-weight: 400;
    font-size: 9px;
    line-height: 16px;
    color: rgba(0, 0, 0, 0.38);
    text-align: right;
    letter-spacing: 0.4px;

    @media screen and (max-width: $mobile) {
      order: 2;
      text-align: start;
      font-size: 11px;
      line-height: 14px;
    };
  }

  .checkbox {
    display: grid;
    place-content: center;
    height: 20px;
    width: 20px;
    border: 1px solid rgba(0, 0, 0, 0.38);
    border-radius: $light-radius;
    cursor: pointer;
    *{ cursor: pointer };

    @media screen and (max-width: $mobile) {
      order: 1;
    };
  };
};

</style>
