<template>
<div class="layout-wrapper">
  <Header />
  <Nuxt />
</div>
</template>

<script>
import Header from "~/components/layout-components/header";
export default {
  name: "default",
  components: {Header}
}
</script>

<style lang="scss" scoped>
@import "assets/css/template";

.layout-wrapper {
  min-height: 100vh;
  background-color: $white-10;

  @media screen and (max-width: $mobile) {
    background-color: $white;
  };
}
</style>
