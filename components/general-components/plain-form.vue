<template>
  <form @submit="submit" class="form row">
    <p class="form__text">{{isPhone ? 'На указанный телефон придет СМС с кодом для входа.' : 'На почту будет отправлена временная ссылка для входа.'}}</p>
    <number-input
      v-if="isPhone"
      holder="Телефон"
      :number-value="phone"
      :change-event="(value) => phone = value"
    />
    <email-input
      v-if="!isPhone"
      holder="Введите email"
      :mail-value="email"
      :change-event="(value) => email = value"
    />
    <plain-button
      :click-event="submit"
      :text="isPhone ? 'Войти по смс-коду' : 'получить ссылку'"
    />
    <checkbox
      label="Авторизуясь на сайте, вы соглашаетесь с <a href='#' class='checkbox-link'>политикой конфиденциальности</a> и даете согласие на обработку персональных данных, а также подтверждаете, что <a href='#' class='checkbox-link'>Ознакомлены и согласны с условиями Договора<a/>"
      :is-checked="isChecked"
      :change-event="() => isChecked = !isChecked"
    />
    <p @click="() => isPhone = !isPhone" class="enterBy">
      {{ isPhone ? 'ВОЙТИ ПО EMAIL' : 'ВОЙТИ С ПОМОЩЬЮ ТЕЛЕФОНА' }}
    </p>
  </form>
</template>

<script>

import PlainButton from "~/components/ui-components/plain-button";
import NumberInput from "~/components/ui-components/inputs/number-input";
import Checkbox from "~/components/ui-components/inputs/checkbox";
import EmailInput from "~/components/ui-components/inputs/email-input";

export default {
  name: "plain-form",
  components: {EmailInput, Checkbox, NumberInput, PlainButton},
  data: () => ({
    phone: '',
    email: '',
    isChecked: false,
    isPhone: true
  }),
  props: {
    title: {
      type: String,
      default: "",
    }
  },
  methods: {
    submit(event) {
      event.preventDefault();
    }
  }
}
</script>

<style lang="scss" scoped>
@import "assets/css/variables";
.form {
  grid-template-columns: 1fr 312px;
  gap: 24px;

  @media screen and (max-width: $mobile) {
    grid-template-columns: 1fr;
  };

  .form__text {
    grid-column: 1/-1;
    font-weight: 700;
    font-size: 20px;
    line-height: 24px;

    @media screen and (max-width: $mobile) {
      font-size: 16px;
      line-height: 16px;
    };
  };

  .enterBy {
    display: grid;
    place-self: center;
    font-weight: 600;
    font-size: 14px;
    line-height: 16px;
    color: $violet;
    text-transform: uppercase;
    cursor: pointer;
  };
};
</style>
