<template>
  <div class="app-header">
    <div class="app-header__text text">
        sf
    </div>
  </div>
</template>
<script>
export default {
  name: "AppHeader",
};
</script>
<style scoped>
.app-header {
  height: 60px;
  display: flex;
  align-items: center;
  background-color: #755858;
  border: solid 1px #000000;
  box-shadow: #000000;
  color: #ffffff;
}

.app-header__text {
  margin-left: 20px;
}
</style>