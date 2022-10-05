<template>
  <div class="documents">
        <!-- <document-item v-for="document in list" :item="document" :key="document.id"></document-item> -->
        <slot></slot>
  </div>
</template>
<script>

export default {
  name: "DocumentsList",
  props: ["list"],
};
</script>
<style lang="scss" scoped>
@import "../assets/sass/vars";

</style>