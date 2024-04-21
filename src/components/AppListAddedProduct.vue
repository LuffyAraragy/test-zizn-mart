<template>
  <div class="app-list-added-products">
    <div class="app-list-added-products__content-product">
      <div
        class="app-list-added-products__product"
        v-for="arr of 3"
        :key="arr.id"
      >
        <div class="text">
          <!-- {{ console.log("Тут должно быть название товара") }} -->
          туту название столбцов
        </div>
        <div class="app-list-added-products__number" v-for="arr of 3" :key="arr.id">
          <!-- {{ console.log("Тут должно быть энное кол во элем") }} -->
          Тут цыфры
        </div>
      </div>
    </div>

    <div class="app-list-added-products__save-final-cost">
      <div class="app-list-added-products__final-cost">
        {{ "итого: 123" }}
      </div>
      <button> Сохранить </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "AppListAddedProducts",
  
};
</script>
<style scoped>
.app-list-added-products {
  
}

.app-list-added-products__content-product {
  display: flex;
}

.app-list-added-products__save-final-cost {
  margin-top: 250px;
  text-align: end;
  border-top: solid 1px #2fa6ea;
}

.app-list-added-products__final-cost {
  margin-top: 18px;
}
</style>