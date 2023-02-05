<template>
  <input
    ref="email"
    :value="mailValue"
    class="mail"
    type="email"
    :placeholder="holder"
    maxlength="100"
    :disabled="isDisabled"
    :style="{
				border: 'solid 1px #ddd',
				...styles,
			}"
    @input="changeEvent($event.target.value)"
  />
</template>
<script>
export default {
	props: {
		// logic prop
		changeEvent: {
			type: Function,
			default: () => null,
		},
		mailValue: {
			type: String,
			default: "",
		},
		isDisabled: {
			type: Boolean,
			default: false,
		},
		holder: {
			type: String,
			default: "",
		},
		// style props
		styles: {
			type: Object,
			default: () => ({}),
		},
	}
};
</script>
<style lang="scss" scoped>
@import "assets/css/variables";

.mail {
  height: 56px;
  width: 100%;
  background-color: $gray;
  padding-left: 15px;
  font-size: 16px;
  line-height: 24px;
  color: $black;
  border-radius: $border;
  outline: none;
  border-color: transparent !important;

  &::placeholder {
    color: rgba(0, 0, 0, 0.38);;
  };
};
</style>
