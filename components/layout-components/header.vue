<template>
<div class="wrapper">
  <div class="content column">
    <logo class="logo"/>
    <div class="header__links column">
      <a href="tel:+74997057893" class="link__text">+7 (499) 705 78 93</a>
      <a href="#" class="link__text">Вопросы и ответы</a>
      <div class="auth__container column">
        <a href="#" class="link__text">Вход</a>
        <div class="vertical__line"/>
        <a href="#" class="link__text">Регистрация</a>
      </div>
    </div>
    <div class="icons__container">
      <a href="#"><call /></a>
      <a href="#"><chat /></a>
      <div><burger /></div>
    </div>
    <div class="mobile__links">
      <a href="#" class="link active__link">Вход</a>
      <a href="#" class="link">Регистрация</a>
    </div>
  </div>
</div>
</template>

<script>

export default {
  name: "header",
  components: {
    logo: () => import('~/static/images/logo.svg?inline'),
    burger: () => import('~/static/images/menu.svg?inline'),
    call: () => import('~/static/images/call.svg?inline'),
    chat: () => import('~/static/images/chat.svg?inline'),
  },
}

</script>

<style lang="scss" scoped>
@import "assets/css/template";

.wrapper {
  background-color: $white;
  box-shadow: 0 1px 10px rgba(0, 0, 0, 0.12), 0 4px 5px rgba(0, 0, 0, 0.14), 0 2px 4px rgba(0, 0, 0, 0.2);

  .content {
    grid-template-columns: auto 1fr;
    align-items: center;
    gap: 100px;
    height: 64px;

    @media screen and (max-width: $tablet) {
      grid-auto-flow: row;
      grid-template-columns: repeat(2, auto);
      justify-content: space-between;
      gap: 35px;
      padding-top: 18px;
      height: 100%;
    };

    .logo {
      @media screen and (max-width: $tablet) {
        height: 24px;
        width: 119px;
      };
    };

    .header__links {
      justify-content: start;
      gap: 85px;

      @media screen and (max-width: $laptop) {
        gap: 65px;
      };

      @media screen and (max-width: $tablet) {
        display: none;
      };

      .auth__container {
        align-items: center;
        gap: 8px;

        .vertical__line {
          height: 100%;
          width: 1px;
          background-color: $black;
        }
      };

      .link__text {
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 16px;
        text-transform: uppercase;
        cursor: pointer;
      };
    };

    .icons__container {
      display: none;

      @media screen and (max-width: $tablet) {
        display: grid;
        grid-auto-flow: column;
        align-items: center;
        gap: 30px;
      };
    };

    .mobile__links {
      display: none;

      @media screen and (max-width: $tablet) {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-column: 1/-1;

        .link {
          text-align: center;
          font-weight: 600;
          font-size: 14px;
          line-height: 16px;
          padding-bottom: 15px;
          border-bottom: 2px solid transparent;
        };

        .active__link {
          border-bottom: 2px solid $black;
        };
      };
    };
  };
};
</style>
