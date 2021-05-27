//
<template>
  <header class="header">
    <div class="header__submenu">
      <div class="header__choose-city">
        <div class="header__choose-city-icon"></div>
        Волгоградская область
      </div>
      <nav class="header__nav-list">
        <router-link to="/about" class="header__nav-list-link">
          Тендеры
        </router-link>
        <router-link to="/" class="header__nav-list-link">
          База подрядчиков
        </router-link>
        <router-link
          to="/"
          class="header__nav-list-link header__nav-list-link_icon"
        >
          Другие сервисы
        </router-link>
      </nav>
    </div>
    <div class="header__main-menu">
      <div class="header__logo">
        <Logo />
      </div>
      <div class="header__button-menu">
        <div class="header__button-menu-icon"></div>
        Каталог
      </div>
      <div class="header__search-bar">
        <SearchBar />
      </div>
      <div class="header__button-list">
        <div class="header__button-list-icon"></div>
        Список
      </div>
      <div class="header__avatar">А</div>
    </div>
  </header>
</template>

<script>
import SearchBar from "@/components/SearchBar";
import Logo from "@/components/Logo";

export default {
  components: {
    SearchBar,
    Logo,
  },
};
</script>

<style lang="scss" scoped>
.header {
  padding: 5px 0;
  color: #708598;
  border: 1px solid #eceff1;
  &__submenu {
    display: flex;
    justify-content: space-between;
    font-size: 12px;
    line-height: 20px;
    padding: 0 85px 3px;
    border-bottom: 1px solid #eceff1;
  }
  &__choose-city-icon {
    position: relative;
    top: 3px;
    display: inline-block;
    width: 16px;
    height: 16px;
    background-image: url("../assets/img/icon/map.svg");
    background-position: 50% 50%;
    background-repeat: no-repeat;
  }
  &__nav-list {
    display: flex;
    &-link {
      margin-right: 24px;
      text-decoration: none;
      color: #708598;
      &:last-child {
        margin-right: 0;
      }
      &_icon:after {
        content: "";
        display: inline-block;
        vertical-align: top;
        position: relative;
        top: 3px;
        display: inline-block;
        width: 16px;
        height: 16px;
        background-image: url("../assets/img/icon/arrow.svg");
        background-position: 50% 50%;
        background-repeat: no-repeat;
      }
    }
  }
  &__main-menu {
    display: flex;
    align-items: center;
    padding: 14px 85px 3px;
  }
  &__logo {
    margin-right: 24px;
  }
  &__button-menu {
    display: flex;
    font-weight: 600;
    font-size: 14px;
    line-height: 24px;
    color: #050f19;
    background: #fed83d;
    padding: 8px 16px 8px 18px;
    border-radius: 4px;
    margin-right: 24px;
    cursor: pointer;
    &-icon {
      position: relative;
      top: 2px;
      display: inline-block;
      width: 20px;
      height: 20px;
      background-image: url("../assets/img/icon/menu.svg");
      background-position: 50% 50%;
      background-repeat: no-repeat;
      margin-right: 8px;
    }
  }
  &__search-bar {
    flex: 1;
    margin-right: 34px;
  }
  &__button-list {
    font-weight: 600;
    font-size: 14px;
    line-height: 24px;
    color: #050f19;
    padding: 5px 15px;
    background: #fafbfc;
    border: 1px solid #eceff1;
    box-sizing: border-box;
    border-radius: 4px;
    margin-right: 24px;
    cursor: pointer;
    &-icon {
      position: relative;
      top: 2px;
      display: inline-block;
      width: 16px;
      height: 20px;
      background-image: url("../assets/img/icon/document.svg");
      background-position: 50% 50%;
      background-repeat: no-repeat;
      margin-right: 8px;
      &:after {
        content: "";
        position: absolute;
        top: -7px;
        right: -7px;
        width: 5px;
        height: 5px;
        background-color: #e92f2f;
        border: 4px solid #fff;
        border-radius: 50%;
      }
    }
  }
  &__avatar {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    font-weight: 600;
    font-size: 14px;
    line-height: 24px;
    border-radius: 50%;
    color: #fff;
    background: #9b51e0;
    cursor: pointer;
  }
}
</style>
