<template>
  <div id="app">
    <HeaderComponent />
    <div class="container">
      <SearchComponent />
      <accordion-component :list="list">
        <template #item="{item}">
          <p class="accordion__content-item" v-html="item.content"></p>
        </template>
      </accordion-component>
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/Header.vue";
import SearchComponent from "@/components/Search.vue";
import AccordionComponent from "@/components/Accordion.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    SearchComponent,
    AccordionComponent
  },
  data() {
    return {
      list: [
        {
          id: 1,
          title: 'Обязательные для всех',
          content: 'content1'
        },
        {
          id: 2,
          title: 'Обязательные для трудоустройства',
          content: 'content2'
        },
        {
          id: 3,
          title: 'Специальные',
          content: 'content3'
        },
      ]
    }
  }
};
</script>
<style lang="scss">
@import "assets/sass/base.scss";
</style>
