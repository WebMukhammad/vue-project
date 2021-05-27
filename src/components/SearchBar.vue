<template>
  <div class="search-bar">
    <div class="search-bar__wrap">
      <label class="search-bar__label">
        <input
          type="text"
          class="search-bar__input"
          placeholder="Хочу найти..."
        />
        <div class="search-bar__input-icon"></div>
      </label>
      <div class="search-bar__list">
        <div class="search-bar__list-item">555</div>
        <div class="search-bar__list-item">555</div>
        <div class="search-bar__list-item">555</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
};
</script>

<style lang="scss" scoped>
.search-bar {
  position: relative;
  height: 40px;
  width: 100%;
  border: 1px solid #eceff1;
  border-radius: 4px;
  &_active &__wrap {
    z-index: 2;
    position: absolute;
    left: -1px;
    right: -1px;
    top: -1px;
    background: #fff;
    border: 1px solid #eceff1;
  }
  &_active &__list {
    display: block;
  }
  &__label {
    position: relative;
    height: 100%;
  }
  &__input {
    width: 100%;
    padding: 7px 13px;
    height: 38px;
    border: none;
    outline: none;
    &::placeholder {
      color: #708598;
      font-size: 14px;
      line-height: 24px;
    }
    &-icon {
      position: absolute;
      top: -6px;
      right: 1px;
      display: inline-block;
      width: 38px;
      height: 38px;
      padding: 10px;
      background-image: url("../assets/img/icon/search.svg");
      background-position: 50% 50%;
      background-repeat: no-repeat;
      background-size: 20px;
      cursor: pointer;
    }
  }
  &__list {
    display: none;
    &-item {
      cursor: pointer;
      padding: 5px 13px;
      border-bottom: 1px solid #eceff1;
      font-size: 14px;
      line-height: 21px;
      border-radius: 4px;
      color: #708598;
      &:last-child {
        border-bottom: none;
      }
    }
  }
}
</style>
