<template>
  <input
    :value="numberValue"
    class="input"
    type="number"
    :maxlength="length"
    :placeholder="holder"
    :disabled="isDisabled"
    :style="{
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
		numberValue: {
			type: String,
			default: "",
		},
		isRequired: {
			type: Boolean,
			default: false,
		},
		isDisabled: {
			type: Boolean,
			default: false,
		},
		length: {
			type: Number,
			default: 256,
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
	},
};
</script>
<style lang="scss" scoped>
@import "assets/css/variables";

.input {
  height: 56px;
  width: 100%;
  background-color: $gray;
  padding-left: 15px;
  font-size: 16px;
  line-height: 24px;
  color: $black;
  border-radius: $border;
  outline: none;
  border-color: transparent;

  &::placeholder {
    color: rgba(0, 0, 0, 0.38);;
  };
};

</style>
