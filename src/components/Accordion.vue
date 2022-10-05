<template>
  <ul class="accordion">
    <li
      v-for="item in list"
      :key="item.id"
      class="accordion__item"
      :data-index="item.id"
    >
      <button
        class="accordion__toggle"
        @click.prevent="toggleTab"
        type="button"
      >
        <div class="accordion__info">
          <img src="../assets/img/icon-arrow.svg" alt="открыть" />
          <h2 class="accordion__title" v-html="item.title"></h2>
        </div>
        <div class="accordion__options">
          <img src="../assets/img/icon-drag.svg" alt="переместить" />
        </div>
      </button>
      <div class="accordion__content">
        <slot name="item" :item="item"></slot>
      </div>
    </li>
  </ul>
</template>
<script>
export default {
  name: "AccordionComponent",
  props: ["list"],
  methods: {
    toggleTab(evt) {
      const target = evt.target.closest(".accordion__item");
      target
        .querySelector(".accordion__toggle")
        .classList.toggle("accordion__toggle--active");
      target
        .querySelector(".accordion__content")
        .classList.toggle("accordion__content--active");
    },
  },
};
</script>
<style lang="scss">
@import "../assets/sass/vars";

.accordion {
  margin: 0;
  padding: 0;
  list-style: none;

  &__item {
    background-color: $color-default-white;
    border: 1px solid #dfe4ef;
    max-width: 1174px;

    + .accordion__item {
      border-top: none;
    }
  }

  &__title {
    font-weight: 500;
    font-size: 15px;
    line-height: 108%;
    margin: 0;
  }

  &__toggle {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: none;
    width: 100%;
    padding: 13px 16px;
    background-color: $color-default-white;
    font-style: normal;
    color: $color-dark-base;
    cursor: pointer;

    img {
      transition: transform $default-transition-settings;
    }

    &--active {
      position: relative;

      .accordion__info {
        img {
          transform: rotate(180deg);
        }
      }
    }
  }

  &__info {
    display: flex;
  }

  &__content {
    max-height: 0;
    overflow: hidden;
    transition: height $default-transition-settings,
      overflow $default-transition-settings;
    padding-left: 16px;

    &--active {
      max-height: none;
      overflow: visible;
    }
  }

  &__content-item {
    font-family: $primary-font;
    font-style: normal;
    font-weight: normal;
    font-weight: 400;
    font-size: 13px;
    line-height: 108%;
    color: $color-dark-base;
    margin: 0;
    padding: 9px 15px;
  }
}
</style>
