<template>
  <div class="wrapper">
    <div class="content row">
      <h1 class="header">Вход</h1>
      <div class="plain__container">
        <plain-form />
      </div>
      <div class="plain__container row">
        <steps-desktop :steps="steps" />
        <steps-mobile :steps="steps" />
      </div>
    </div>
  </div>
</template>

<script>
import PlainForm from "~/components/general-components/plain-form";
import ArrowDown from "~/static/images/arrow-down.svg?inline";
import StepsMobile from "~/components/page-components/components/steps-mobile";
import StepsDesktop from "~/components/page-components/components/steps-desktop";

export default {
  name: "home-page",
  components: { StepsDesktop, StepsMobile, PlainForm, ArrowDown },
  data: () => ({
    steps: [
      { src: require('/assets/images/home-page/step-1.png'), text: 'Звонок, <br/> регистрация, заказ' },
      { src: require('/assets/images/home-page/step-2.png'), text: 'Консультация' },
      { src: require('/assets/images/home-page/step-3.png'), text: 'Оплата заказа, <br/> загрузка документов' },
      { src: require('/assets/images/home-page/step-4.png'), text: 'Проверка документов, <br/> заполнение и отправка декларации' },
      { src: require('/assets/images/home-page/step-5.png'), text: 'Поступление денег <br/> от ФНС' }
    ]
  })
}
</script>

<style lang="scss" scoped>
@import "assets/css/template";

.wrapper {
  padding: 40px 0;

  @media screen and (max-width: $mobile) {
    padding: 35px 0;
  };

  .content {
    gap: 30px;

    @media screen and (max-width: $mobile) {
      gap: 40px;
    };

    .header {
      @media screen and (max-width: $tablet) {
        display: none;
      };
    }

    .plain__container {
      gap: 25px;
      padding: 28px 36px 44px;
      border: 2px solid #ECEFF1;
      border-radius: $border;
      background-color: $white;

      @media screen and (max-width: $mobile) {
        padding: 0;
        border: none;
      };
    };
  };
};
</style>
