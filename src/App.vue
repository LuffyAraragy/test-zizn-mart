<template>
    <PageHome></PageHome>
</template>

<script>
import PageHome from "./page/PageHome.vue";
export default {
  name: "App",
  components: { PageHome },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  background-color: #e5e5e5;
}

select {
  border: none;
}

input {
  border: none;
}

.container {
  max-width: 1400px;
  /* margin: 0 auto; */
  padding: 0 23px;
}

.block {
  display: flex;
  /* gap: 20px; */
}

.text {
  color: #222222;
}

.text--blue {
  color: #0170ae;
}

.text--white {
  color: #ffffff;
}

.input {
  outline: none;
  padding: 12px;
  font-size: 16px;
  border-bottom: solid 2px #2fa6ea;
}

.button {
  padding: 12px;
  max-width: 394px;
  width: 100%;
  color: #ffffff;
  font-size: 16px;
  border: none;
  border-radius: 10px;
  box-sizing: border-box;
}

.button--blue {
  background-color: #2fa6ea;
}

.button--green {
  background-color: #61a91a;
}
</style>
