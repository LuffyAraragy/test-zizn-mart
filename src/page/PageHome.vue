<template>
  <div class="page-home">
    <AppHeader> </AppHeader>
    <AppFormProduct></AppFormProduct>
    <AppFooter> </AppFooter>
  </div>
</template>
<script>
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "../components/AppFooter.vue";
import AppFormProduct from "@/components/AppFormProduct.vue";

export default {
  name: "PageHome",
  components: {
    AppFooter,
    AppHeader,
    AppFormProduct,
  },
};
</script>
<style scoped>
.page-home {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>