<template>
  <div class="documents">
        <document-item v-for="document in list" :item="document" :key="document.id"></document-item>
  </div>
</template>
<script>
import DocumentItem from "@/components/DocumentItem.vue";

export default {
  name: "DocumentsList",
  props: ["list"],
  components: {
    DocumentItem
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/sass/vars";

</style>