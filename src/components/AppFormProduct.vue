<template>
  <div class="app-product container">
    <div class="app-product__form">
      <label for="pet-select">Выберите продукцию</label>
      <select class="input select" name="pets" id="pet-select">
        <option
          :value="product.title"
          v-for="product of dataProducts"
          :key="product.id"
        >
          {{ product.title }}
        </option>
      </select>

      <div class="text">Введите количество</div>
      <input class="input" type="text" placeholder="0" v-model="numberThings" />
      <button
        class="button button--blue"
        @click="addItemProduct(numberThings, dataProducts)"
      >
        Добавить
      </button>
    </div>

    <div class="app-product__content-info">
      <div class="app-product__block">
        <div class="app-product__text text text--blue">Название товара</div>
        <div class="block">
          <div class="app-product__text item text text--blue">Количество</div>
          <div class="app-product__text item text text--blue">Стоимость</div>
        </div>
      </div>
      <div class="app-product__block-info">
        <div
          class="app-product__block-item"
          v-for="product in bufferProducts"
          :key="product.id"
        >
          <div class="app-product__title">{{ product.title }}</div>
          <div class="app-product__block-number-price">
            <div class="item">{{ product.number }} шт.</div>
            <div class="item">{{ product.price }}</div>
          </div>
        </div>
      </div>

      <div class="app-product__save-final-cost">
        <div class="app-product__final-cost">
          Итого: {{ calculatingPurchaseAmount }}
        </div>
        <div class="app-product__button-block">
          <button
            class="button button--green app-product__button"
            @click="preparationShipment(bufferProducts)"
          >
            Сохранить
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "AppFormProduct",
  data() {
    return {
      dataProducts: null,
      numberThings: null,
      nameColumns: ["Название товара", "Количество", "Стоимость"],
      bufferProducts: [],
      sum: null,
      bufferSum: null,
      products: [],
    };
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get(
          "https://dev-su.eda1.ru/test_task/products.php"
        );
        console.log(response.data);
        this.dataProducts = response.data.products;
        // обработка полученных данных
      } catch (error) {
        console.error(error);
      }
    },

    async postData(data) {
      try {
        const response = await axios.post(
          "https://dev-su.eda1.ru/test_task/save.php",
          data
        );
        console.log(response);
        alert("Ваш код заказа " + response.data.code);
        console.log(response.data);
        // обработка ответа после отправки данных
      } catch (error) {
        console.error(error);
      }
    },

    preparationShipment(arrs) {
      for (let arr of arrs) {
        this.products.push({
          product_id: arr.id,
          quantity: Number(arr.number),
        });
      }
      this.postData(this.products);
    },

    addItemProduct(number, products) {
      let select = document.querySelector("select");
      for (let product of products) {
        if (product.title == select.value) {
          console.log(product.title);
          this.bufferProducts.push({
            id: product.id,
            title: product.title,
            number: number,
            price: product.price * number,
          });
        }
      }
    },
  },

  computed: {
    calculatingPurchaseAmount() {
      return this.bufferProducts.reduce(
        (acc, curr) => acc + curr.price * curr.number,
        0
      );
    },
  },
  created() {
    this.fetchData();
  },
};
</script>
<style scoped>
.app-product {
  padding-top: 38px;
  display: flex;
  justify-content: center;
  gap: 50px;
}

.app-product__block-number-price {
  display: flex;
}

.app-product__content-info {
  width: 100%;
  max-width: 600px;
}

.app-product__form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.app-product__block {
  display: flex;
  justify-content: space-between;
}

.app-product__block-item {
  display: flex;
  justify-content: space-between;
}

.item {
  width: 100px;
  max-width: 100%;
  text-align: end;
}

.input  {
  color: #2fa6ea;
}

.app-product__title {
  display: flex;
}

.app-product__save-final-cost {
  margin-top: 250px;
  text-align: end;
  border-top: solid 1px #2fa6ea;
}

.app-product__final-cost {
  margin-top: 18px;
}

.app-product__button-block {
  text-align: center;
}

@media (max-width: 650px) {
  .app-product {
    flex-direction: column;
  }

  .app-product__block {
    display: none;
  }

  .app-product__block-item {
    /* display: block; */
    flex-direction: column;
    gap: 20px;
  }

  .app-product__block-number-price {
    justify-content: space-between;
  }

  .item {
    text-align: start;
  }
}
</style>