<template>
  <div :class="['search-bar', { 'search-bar_active': query }]">
    <div class="search-bar__wrap">
      <label class="search-bar__label">
        <input
          type="text"
          v-model="query"
          class="search-bar__input"
          placeholder="Хочу найти..."
          @input="onInput"
        />
        <div
          v-if="loading"
          class="search-bar__input-icon search-bar__input-icon_loading"
        ></div>
        <div class="search-bar__input-icon search-bar__input-icon_search"></div>
      </label>
      <div v-if="list.length" class="search-bar__list">
        <div
          v-for="(item, index) in list"
          :key="index"
          class="search-bar__list-item"
        >
          {{ item }}
        </div>
      </div>
      <div v-else-if="!loading" class="search-bar__empty">
        по запросу ничего не найдено
      </div>
      <div class="search-bar__error" v-else>{{ error }}</div>
    </div>
  </div>
</template>

<script>
import debounce from "lodash.debounce";

export default {
  name: "SearchBar",
  data() {
    return {
      query: null,
      loading: false,
      error: null,
      list: [],
    };
  },
  created() {
    this.requesData = debounce(this.requesData, 300);
  },
  methods: {
    onInput() {
      this.error = null;
      this.loading = true;
      this.requesData();
    },
    async requesData() {
      try {
        // не нашел более лучшее апи
        const result = await fetch(
          `https://api.bukvarix.com/v1/keywords/?api_key=free&format=json&json_type=array&num=5&q=${encodeURI(
            this.query
          )}`
        );
        let response = await result.json();
        response = response.map((el) => (el.length ? el[0] : el));
        this.list = response || [];
        this.loading = false;
      } catch (e) {
        console.log("При получении фраз произошла ошибка", e);
        this.error = "При получении фраз произошла ошибка";
      }
    },
  },
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
  &_active &__list,
  &_active &__empty,
  &_active &__error {
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
      background-position: 50% 50%;
      background-repeat: no-repeat;
      background-size: 20px;
      cursor: pointer;
      &_search {
        top: -6px;
        right: 1px;
        width: 38px;
        height: 38px;
        padding: 10px;
        background-image: url("../assets/img/icon/search.svg");
      }
      &_loading {
        top: 5px;
        right: 42px;
        width: 16px;
        height: 16px;
        background-size: contain;
        background-image: url("../assets/img/icon/loading-oval.svg");
      }
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
  &__empty,
  &__error {
    display: none;
    font-size: 14px;
    line-height: 21px;
    padding: 5px 13px;
  }
}
</style>
