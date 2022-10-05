<template>
  <div id="app">
    <header-component></header-component>
    <div class="container">
      <search-component></search-component>
      <accordion-component :list="list">
        <template #item="{item}">
          <documents-list :list="item.documents"></documents-list>
          <!-- <document-item :item="item.documents"></document-item> -->
        </template>
      </accordion-component>
      <document-item
        :item="{
            title: 'Тестовое задание кандидата',
            description: 'Россия, Белоруссия, Украина, администратор филиала, повар-сушист, повар-пиццмейкер, повар горячего цеха',
        }"
      ></document-item>
       <document-item
        :item="{
            title: 'Трудовой договор',
             }"
      ></document-item>
       <document-item
        :item="{
            title: 'Медкнижка',
             }"
      ></document-item>
      
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/Header.vue";
import SearchComponent from "@/components/Search.vue";
import AccordionComponent from "@/components/Accordion.vue";
import DocumentsList from "@/components/DocumentsList.vue";
import DocumentItem from "@/components/DocumentItem.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    SearchComponent,
    AccordionComponent,
    DocumentsList,
    DocumentItem
  },
  data() {
    return {
      list: [
        {
          id: 1,
          title: 'Обязательные для всех',
          description: 'Документы, обязательные для всех сотрудников без исключения',
          documents: [
            {
              id: 'doc1',
              title: 'Паспорт',
              description: 'Для всех',
              required: true
            },
            {
              id: 'doc2',
              title: 'ИНН',
              description: 'Для всех',
              required: true
            },
          ],            
        },
        {
          id: 2,
          title: 'Обязательные для трудоустройства',
          description: 'Документы, без которых невозможно трудоустройство человека на какую бы то ни было должность в компании вне зависимости от граж',
          documents: [
            {
              id: 'doс3',
              title: 'Паспорт',
              description: 'Для всех',
              required: true
            },
            {
              id: 'doc4',
              title: 'ИНН',
              description: 'Для всех',
              required: true
            },
          ],   
        },
        {
          id: 3,
          title: 'Специальные',
          documents: [
            {
              id: 'doc5',
              title: 'Паспорт',
              description: 'Для всех',
              required: true
            },
            {
              id: 'doc6',
              title: 'ИНН',
              description: 'Для всех',
              required: true
            },
          ],   
        },
      ]
    }
  }
};
</script>
<style lang="scss">
@import "assets/sass/base.scss";
</style>
