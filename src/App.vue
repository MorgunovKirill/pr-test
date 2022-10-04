<template>
  <div id="app">
    <HeaderComponent />
    <div class="container">
      <SearchComponent />
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/Header.vue";
import SearchComponent from "@/components/Search.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    SearchComponent,
  },
};
</script>
<style lang="scss">
@import "assets/sass/base.scss";
</style>
