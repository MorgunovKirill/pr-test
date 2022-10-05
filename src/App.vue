<template>
  <div id="app">
    <header-component></header-component>
    <div class="container">
      <search-component></search-component>
      <accordion-component :list="list">
        <template #item="{ item }">
          <documents-list>
            <draggable
              :list="item.documents"
              group="documentsGroup"
              ghostClass="on-drag"
              animation="400"
              :options="{handle:'.handle'}"
            >
              <document-item
                v-for="document in item.documents"
                :item="document"
                :key="document.id"
              ></document-item>
            </draggable>
          </documents-list>
        </template>
      </accordion-component>
      <documents-list>
        <draggable 
        :list="unClassifiedList" 
        group="documentsGroup" 
        ghostClass="on-drag" 
        animation="400"
        :options="{handle:'.handle'}"
        >
          <document-item
            v-for="document in unClassifiedList"
            :item="document"
            :key="document.id"
          ></document-item>
        </draggable>
      </documents-list>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
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
    DocumentItem,
    draggable,
  },
  data() {
    return {
      list: [
        {
          id: 1,
          title: "Обязательные для всех",
          description:
            "Документы, обязательные для всех сотрудников без исключения",
          documents: [
            {
              id: "doc1",
              title: "Паспорт",
              description: "Для всех",
              required: true,
            },
            {
              id: "doc2",
              title: "ИНН",
              description: "Для всех",
              required: true,
            },
          ],
        },
        {
          id: 2,
          title: "Обязательные для трудоустройства",
          description:
            "Документы, без которых невозможно трудоустройство человека на какую бы то ни было должность в компании вне зависимости от граж",
          documents: [
            {
              id: "doс3",
              title: "Паспорт",
              description: "Для всех",
              required: true,
            },
            {
              id: "doc4",
              title: "ИНН",
              description: "Для всех",
              required: true,
            },
          ],
        },
        {
          id: 3,
          title: "Специальные",
          documents: [
            {
              id: "doc5",
              title: "Паспорт",
              description: "Для всех",
              required: true,
            },
            {
              id: "doc6",
              title: "ИНН",
              description: "Для всех",
              required: true,
            },
          ],
        },
      ],
      unClassifiedList: [
        {
          id: "doc7",
          title: "Тестовое задание кандидата",
          description:
            "Россия, Белоруссия, Украина, администратор филиала, повар-сушист, повар-пиццмейкер, повар горячего цеха",
        },
        {
          id: "doc8",
          title: "Трудовой договор",
        },
        {
          id: "doc9",
          title: "Медкнижка",
        },
      ],
    };
  },
};
</script>
<style lang="scss">
@import "assets/sass/base.scss";
</style>
