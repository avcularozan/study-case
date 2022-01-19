<template>
  <div>
    <fieldset class="quantity-box">
      <label class="quantity-label" for="product-detail-quantity-input">
        Adet
      </label>
      <div class="quantity-detail">
        <div class="quantity-input">
          <input
            type="number"
            id="quantity"
            name="quantity"
            v-model="quantity"
            min="1"
          />
        </div>
        <span class="stock-quantity">
          Stok Adedi: <span>{{ model.stockQuantity }}</span>
        </span>
      </div>
    </fieldset>
  </div>
</template>

<script>
export default {
  name: "QuantitySection",
  components: {},
  props: ["model"],
  data() {
    return {
      quantity: 1,
    };
  },
  created() {
    this.quantity = this.model.baremList[0].minimumQuantity;
  },
  watch: {
    quantity(newValue) {
      this.$emit("data", newValue);
    },
  },
};
</script>

<style>
.barem-box {
  padding: 12px 0 0 13px;
  background-color: #f5f5f5;
}
.total-price {
  float: left;
  font-weight: 300;
  width: 67px;
  margin-bottom: 0;
  margin-top: 7px;
  font-size: 12px;
  color: #000;
  line-height: 17px;
  text-align: right;
  text-align: right;
}
.total-price p {
  font-weight: 500;
}
.barem-list {
  float: left;
  width: 380px;
  margin-left: 15px;
}
.quantity-box {
  padding: 15px 0 10px 13px;
  background-color: #f5f5f5;
}
.quantity-label {
  line-height: 31px;
  padding-top: 1px;
  float: left;
  font-weight: 500;
  width: 67px;
  margin-bottom: 0;
  font-size: 12px;
  color: #000;
  text-align: right;
}
.quantity-detail {
  float: left;
  width: 384px;
  margin-left: 15px;
  position: relative;
}
.quantity-input {
  width: 120px;
  border: 1px solid #bebebe;
  display: inline-block;
  width: 70px;
  height: 31px;
  font-size: 14px;
}
.quantity-input input {
  float: left;
  text-align: center;
  width: 67px;
  padding: 0;
  height: 29px;
  font-size: 14px;
  font-weight: 500;
  line-height: 29px;
  border: none;
  background-color: #fff;
}
.stock-quantity {
  padding: 3px 5px;
  font-size: 12px;
  color: #38b649;
  float: right;
  margin-right: 20px;
  margin-top: 6px;
  background-color: #fafafa;
  border: 1px solid #38b649;
  border-radius: 2px;
}
.quantity-error {
  display: block;
  margin-top: 6px;
  font-size: 11px;
  color: #ea222f;
}
</style>
