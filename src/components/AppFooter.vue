<template>
  <div class="app-footer">
    <div class="text text--white app-footer__text">Very intresting tail</div>
  </div>
</template>
<script>
export default {
  name: "AppFooter",
};
</script>
<style scoped>
.app-footer {
  min-height: 220px;
  margin-top: auto;
  display: flex;
  align-items: flex-end;
  justify-content: flex-end;
  background-color: #222222;
  color: #ffffff;
}

.app-footer__text {
  margin-right: 23px;
  margin-bottom: 20px;
}
</style>