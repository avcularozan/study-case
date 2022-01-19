<template>
  <form class="product-detail-form" @submit.prevent="addToBasket">
    <div class="button-holder">
      <button type="submit" class="button is-secondary" :disabled="isDisabled">
        SEPETE EKLE
      </button>
      <span>Ödeme Yöntemleri</span>
    </div>
  </form>
</template>

<script>
export default {
  name: "ProductDetailFrom",
  components: {},
  data() {
    return {
      model: {},
    };
  },
  methods: {
    addToBasket() {
      console.log("model", this.model);
    },
  },
  computed: {
    isDisabled() {
      return false;
    },
  },
};
</script>

<style scope>
.product-detail-form {
  float: left;
  width: 480px;
}
.button-holder {
  display: flex;
  align-items: center;
  width: 80%;
  margin: 15px 0 0 100px;
}
.button-holder > button {
  float: left;
  width: 180px;
  line-height: 45px;
  height: 46px;
  padding-bottom: 1px;
  font-weight: bold;
}
.button-holder > button:disabled {
  opacity: 0.5;
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";
  filter: alpha(opacity=50);
  cursor: default;
}
.button-holder > span {
  margin-left: 10px;
  font-size: 12px;
  color: #0063cf;
  cursor: pointer;
}
</style>
