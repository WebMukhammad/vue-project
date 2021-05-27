<template>
  <router-link to="/" class="logo">
    <img class="logo__img" src="../assets/img/icon/logo.svg" alt="" />
  </router-link>
</template>

<script>
export default {
  name: "Logo",
};
</script>

<style lang="scss" scoped>
.logo {
  width: 221px;
  height: 48px;
  &__img {
    max-width: 100%;
    max-height: 100%;
  }
}
</style>
