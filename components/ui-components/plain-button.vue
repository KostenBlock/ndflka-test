<template>
	<button
		ref="btn"
		:style="[
			{
				opacity: isDisabled ? '0.7' : '1',
			},
			isDisabled ? { backgroundColor: '#F8F8F8', border: '1px solid #333', color: '#a3a3a3' } : '',
		]"
		:disabled="isDisabled"
		@mouseover="
			$refs.btn ? ($refs.btn.style.boxShadow = '0px 4px 6px rgba(74, 67, 67, 0.3)') : null;
			$refs.btn ? ($refs.btn.style.transform = 'scale(1.05)') : null;
		"
		@mouseout="
			$refs.btn ? ($refs.btn.style.boxShadow = 'none') : null;
			$refs.btn ? ($refs.btn.style.transform = 'scale(1)') : null;
		"
		@click="
			clickEvent($event);
			$refs.btn ? ($refs.btn.style.boxShadow = 'none') : null;
			$refs.btn ? ($refs.btn.style.transform = 'scale(1)') : null;
		"
	>
		{{ text }}
		<slot />
	</button>
</template>
<script>
export default {
	props: {
		// text config
		text: {
			type: String,
			default: "",
		},
		// event config
		isDisabled: {
			type: Boolean,
			default: false,
		},
		isActive: {
			type: Boolean,
			default: false,
		},
		clickEvent: {
			type: Function,
			default: () => {},
		},
	},
};
</script>
<style lang="scss" scoped>
@import "assets/css/template";

button {
  font-family: 'Source Sans Pro', serif;
	font-size: 16px;
	color: $white;
  background-color: $violet;
  width: 100%;
  height: 56px;
  transition: box-shadow $time, transform $time, background-color $time, color $time;
  border-radius: $border;
  text-transform: uppercase;
}
</style>
